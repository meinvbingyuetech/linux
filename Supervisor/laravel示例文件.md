```php

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

            // 获取等待转换的数据
            $result = $this->speech_service->getWechatVoiceNoTransData();

            // 如果没有数据需要转换，则继续循环
            if (count($result)==0) {
                $this->info('没有需要转换的数据');
                sleep(60);
                continue;
            }

            // 循环下载文件
            foreach ($result as $item) {
                $file = $this->wechat_service->downVoice($item['id']);
                $this->info("下载文件：".$file);
            }
            sleep(60);

        }

    }

}


```
