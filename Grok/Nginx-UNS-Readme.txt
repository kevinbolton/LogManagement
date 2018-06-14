# Grok-Nginx-UNS
Tested in ELK V.6.1

[Nginx Log Format]
log_format main '$remote_addr - $remote_user [$time_local] $request_time "$host" "$request" $status $body_bytes_sent "$http_referer" "$http_user_agent" "$http_x_forwarded_for"';

[Sample of Nginx log]
1.26.20.13 - - [18/Jan/2018:00:00:00 +0800] 0.102 "www.one.com" "GET /sure/index.do?method=info&type=1&id=1 HTTP/1.1" 200 3022 "https://www.one.com/index.html?v=c76c496fa" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36" "12.26.20.13"

182.246.220.143 - Kevin - [18/Jan/2018:00:00:00 +0800] 0.102 "www.one.com" "GET /sure/index.do?method=info&type=1&id=1 HTTP/1.1" 200 3022 "https://www.one.com/index.html?v=c76c496fa" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36" "12.26.20.13"

12.0.1.21 - - [18/Jan/2018:00:00:02 +0800] 0.001 "_" "GET /" 200 2973 "-" "-" "-"

[Grok pattern]

Export from http://grokconstructor.appspot.com :
 %{IPORHOST:nginx.access.remote_ip_list} - %{DATA:nginx.access.user_name} \[%{HTTPDATE:nginx.access.time}\] %{NUMBER:request_time:float} "(?:%{IPORHOST:serveraddr}|%{DATA:rawserveraddr})" "(?:%{WORD:nginx.access.method} %{NOTSPACE:nginx.access.url}(?: HTTP/%{NUMBER:nginx.access.http_version})?|%{WORD:nginx.access.method} %{DATA:rawrequest})" %{NUMBER:nginx.access.response_code} %{NUMBER:nginx.access.body_sent.bytes} "%{DATA:nginx.access.referrer}" "%{DATA:nginx.access.agent}" "(?:%{IPORHOST:http_x_forwarded_for}|%{DATA:rawhttp_x_forwarded_for})"

Put into ELK(Without "") : 
%{IPORHOST:nginx.access.remote_ip_list} - %{DATA:nginx.access.user_name} \[%{HTTPDATE:nginx.access.time}\] %{NUMBER:request_time:float} \"(?:%{IPORHOST:serveraddr}|%{DATA:rawserveraddr})\" \"(?:%{WORD:nginx.access.method} %{NOTSPACE:nginx.access.url}(?: HTTP/%{NUMBER:nginx.access.http_version})?|%{WORD:nginx.access.method} %{DATA:rawrequest})\" %{NUMBER:nginx.access.response_code} %{NUMBER:nginx.access.body_sent.bytes} \"%{DATA:nginx.access.referrer}\" \"%{DATA:nginx.access.agent}\" \"(?:%{IPORHOST:http_x_forwarded_for}|%{DATA:rawhttp_x_forwarded_for})\"
