Tested in Graylog V.2.4.3

[Log Format]
#access_log  logs/access.log;
log_format access [$time_local] ‘$remote_addr – $remote_user [$request_time] [$upstream_response_time] - “$request” ‘‘[$status] $body_bytes_sent “$http_referer” ‘‘”$http_user_agent” $http_x_forwarded_for’;

[Sample of Nginx log]
[05/Jun/2018:03:26:28 +0800]‘1.1.1.1–-[0.019][0.020]-“GET /WinQuery/Details.aspx?ID=83 HTTP/1.1”‘‘[200]10226“http://www.vip.com/WinQuery/Details.aspx?ID=83”‘‘”Mozilla/5.0 (Windows; U; Windows NT 5.1; pt-PT; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2 (.NET CLR 3.5.30729)”-’
[05/Jun/2018:03:26:29 +0800]‘1.1.1.1–-[0.008][0.007]-“GET /WinQuery/Details.aspx?ID=83'A=0 HTTP/1.1”‘‘[302]171“http://www.vip.com/WinQuery/Details.aspx?ID=83'A=0”‘‘”Mozilla/5.0 (Windows; U; Windows NT 5.1; pt-PT; rv:1.9.1.2) Gecko/20090729 Firefox/3.5.2 (.NET CLR 3.5.30729)”-’
[05/Jun/2018:03:26:36 +0800]‘1.1.1.1–-[0.001][-]-“GET / HTTP/1.1”‘‘[200]172436“-”‘‘”Load Balancer Agent”-’
[06/Jun/2018:07:51:36 +0800]‘1.1.5.2–-[0.000][-]-“GET / HTTP/1.1”‘‘[200]26006“http://www.cai.net/”‘‘”Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; Tablet PC 2.0)”unknown,182.118.20.146’
