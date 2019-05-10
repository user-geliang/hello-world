# hello-world
hello-world

print('hello word!')

这里是第一个helloworld项目，学习使用github

#使用python2的pip
python2 -m pip

#ubantu配置 shadowsocks报错问题
用vim打开文件：vim /usr/local/lib/python2.7/dist-packages/shadowsocks/crypto/openssl.py (该路径请根据自己的系统情况自行修改，如果不知道该文件在哪里的话，可以使用find命令查找文件位置)
跳转到52行（shadowsocks2.8.2版本，其他版本搜索一下cleanup）
进入编辑模式
将第52行libcrypto.EVP_CIPHER_CTX_cleanup.argtypes = (c_void_p,) 
改为libcrypto.EVP_CIPHER_CTX_reset.argtypes = (c_void_p,)
再次搜索cleanup（全文件共2处，此处位于111行），将libcrypto.EVP_CIPHER_CTX_cleanup(self._ctx) 
改为libcrypto.EVP_CIPHER_CTX_reset(self._ctx)
保存并退出
启动shadowsocks服务：service shadowsocks start 或 sslocal -c ss配置文件目录
问题解决
