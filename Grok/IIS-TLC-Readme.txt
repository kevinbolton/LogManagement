Tested in Graylog V.2.4.3

[Log Format]
#Fields: date time s-sitename s-computername s-ip cs-method cs-uri-stem cs-uri-query s-port cs-username c-ip cs-version cs(User-Agent) cs(Referer) cs-host sc-status sc-substatus sc-win32-status sc-bytes cs-bytes time-taken

[Sample of Nginx log]
2018-06-05 12:00:25 W3SVC4 Prod-WEB 10.0.0.4 GET /3D/ - 80 - 10.0.0.12 HTTP/1.0 Mozilla/5.0+(Windows+NT+10.0;+WOW64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/55.0.2883.87+Safari/537.36 http://warn.chrome.360.cn/warn/?DA== www.vip.com 200 0 0 122745 952 45
