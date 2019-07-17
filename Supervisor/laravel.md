- app\Console\Kernel.php
```php
namespace App\Console;

use Illuminate\Console\Scheduling\Schedule;
use Illuminate\Foundation\Console\Kernel as ConsoleKernel;

class Kernel extends ConsoleKernel
{
    protected $commands = [
        //
    ];


    protected function schedule(Schedule $schedule)
    {
         // 每分钟执行
         $schedule->command('command:wechat-voice')
                  ->everyMinute();
    }

    protected function commands()
    {
        $this->load(__DIR__.'/Commands');

        require base_path('routes/console.php');
    }
}

```

----

- app\Console\Commands\WechatVoice.php
```php
<?php

namespace App\Console\Commands;

use App\Services\Admin\SpeechService;
use App\Services\WechatService;
use Illuminate\Console\Command;

class WechatVoice extends Command
{
    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'command:wechat-voice';

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = '微信语音下载并转换格式';

    public $wechat_service = null;
    public $speech_service = null;

    /**
     * Create a new command instance.
     *
     * @return void
     */
    public function __construct(SpeechService $speech_service, WechatService $wechat_service)
    {
        parent::__construct();

        $this->speech_service = $speech_service;
        $this->wechat_service = $wechat_service;
    }

    /**
     * Execute the console command.
     *
     * @return mixed
     */
    public function handle()
    {
        while (1) {

            // 获取没有转换的数据
            $result = $this->speech_service->getWechatVoiceNoTransData();
            foreach ($result as $item) {

                if (!empty($item['wx_audio'])) {
                    try {
                        $file = $this->wechat_service->downVoice($item['id'], $item['wx_audio']);
                        $this->info("下载文件：".$file);

                    } catch (\Exception $exception) {
                        $this->speech_service->update([
                            'id'=>$item['id'],
                            'wx_audio_trans'=>'fail'
                        ]);
                        $this->error("下载失败，speech_id：".$item['id']);
                    }
                }

                sleep(2);
            }
        }
    }

}

```
