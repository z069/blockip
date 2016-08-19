禁止恶意访问通过穷举法暴力破解账号密码的Nginx配置文件


本配置文件通过Nginx的nginx.conf文件调用实现禁止有恶意行为的IP和IP段访问

注意：因为Nginx的安装路径各不相同，本文的配置文件路径以/usr/local/nginx/conf为例，请注意将命令中红色的字体，修改为适合你的路径，切记！！！

一、下载配置文件
使用下面的命令下载配置文件

wget -O /usr/local/nginx/conf/blockip.conf https://raw.githubusercontent.com/z069/blockip/master/blockip.conf
chmod +x /usr/local/nginx/conf/blockip.conf

二、修改Nginx.conf



在使用blockip.conf前，需要先对nginx.conf文件进行修改在http段的某位括号前加入：
	include blockip.conf; 


三、重启Nginx
/usr/local/nginx/sbin/nginx -s reload


四、更新blockip.conf
因为恶意行为的IP经常更换，所以建议每过一段时间更新一下配置文件，可以手动更新或设定计划任务自动更新
手动更新：
wget -O /usr/local/nginx/conf/blockip.conf https://raw.githubusercontent.com/z069/blockip/master/blockip.conf

自动更新：
每天晚上的18点更新配置文件
0 18 * * * wget -O /usr/local/nginx-1.10/conf/blockip.conf https://raw.githubusercontent.com/z069/blockip/master/blockip.conf
