```
curl http://127.0.0.1:8000/v1/login

curl http://127.0.0.1:8000/welcome\?firstname\=jason


curl -X POST http://127.0.0.1:8000/form_post -H "Content-Type:application/x-www-form-urlencoded" -d "message=hello&nick=rsj217" | python -m json.tool

curl -v --form user=user --form password=password http://localhost:8080/login


上传单个文件
curl -X POST http://127.0.0.1:8000/upload -F "upload=@/Users/ghost/Desktop/pic.jpg" -H "Content-Type: multipart/form-data"

上传多个文件
curl -X POST http://127.0.0.1:8000/multi/upload -F "upload=@/Users/ghost/Desktop/pic.jpg" -F "upload=@/Users/ghost/Desktop/journey.png" -H "Content-Type: multipart/form-data"



curl -X POST http://127.0.0.1:8000/login -H "Content-Type:application/x-www-form-urlencoded" -d "username=rsj217&passwd=123&age=21" | python -m json.tool




curl -X POST http://127.0.0.1:8000/login -H "Content-Type:application/json" -d '{"username": "rsj217", "passwd": "123", "age": 21}' | python -m json.tool


curl  http://127.0.0.1:8000/render\?content_type\=json
{"passwd":"123","user":"rsj217"}


curl  http://127.0.0.1:8000/render\?content_type\=xml
<map><user>rsj217</user><passwd>123</passwd></map>%


```
