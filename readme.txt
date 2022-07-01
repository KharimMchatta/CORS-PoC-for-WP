1. First of all you should check if the sie is vulnerable to this type of vulnerbaility by just doing the following
   a. add /wp-json/
   b. add header Origin: http://test.com or any domain of your liking
 as shown below
-------------------------------------------------------------------------------------------------------------------------------------
GET /wp-json/ HTTP/2                    //adding /wp-json/
Host: target.com
Origin: http://test.com                //adding origin header
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: https://target.com
------------------------------------------------------------------------------------------------------------------------------------------




once everything is added just send the request to the target and you will get the following response or similar
-----------------------------------------------------------------------------------------------------------------------------------------
HTTP/2 200 OK
Content-Type: application/json; charset=UTF-8
X-Robots-Tag: noindex
Link: <https://target.com/wp-json/>; rel="https://api.w.org/"
X-Content-Type-Options: nosniff
Access-Control-Expose-Headers: X-WP-Total, X-WP-TotalPages, Link
Access-Control-Allow-Headers: Authorization, X-WP-Nonce, Content-Disposition, Content-MD5, Content-Type
Allow: GET
Access-Control-Allow-Origin: http://test.com
Access-Control-Allow-Methods: OPTIONS, GET, POST, PUT, PATCH, DELETE
Access-Control-Allow-Credentials: true

the most important thing to look for is this section
Allow: GET
Access-Control-Allow-Origin: http://test.com
Access-Control-Allow-Methods: OPTIONS, GET, POST, PUT, PATCH, DELETE
Access-Control-Allow-Credentials: true


2. once the bug is found then you go and exploit it using the cors.html file, just replace target.com with your target
