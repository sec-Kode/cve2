# Any file deletion vulnerability exists in ZenTaoPMS-20.0.beta2

There is a vulnerability in the delete method in ZenTaoPMS-20.0.beta2-php7.2_7.4\zentaopms\module\backup\control.php.

![image](https://github.com/sec-Kode/cve2/assets/46676387/27165e11-c723-4d00-8b87-7209c92af813)
There is an unlink dangerous function here, and there is no filtering, so any file deletion operation can be performed.

And it will be deleted here in the form of the entire folder.

For the convenience of demonstration, create a folder named kode in the F:\phpstudy_pro\WWW\127.0.0.1\ZenTaoPMS-20.0.beta2-php7.2_7.4\zentaopms directory

![image](https://github.com/sec-Kode/cve2/assets/46676387/b1f83c55-94f2-4f1b-95d3-186d0e260144)

This vulnerability requires logging into the website backend to operate.

After logging in to the backend, we can use the following payload to delete the entire kode folder.
