##### make an empty file with specific name and size
```bash
truncate -s <filesize> <filename>
```
##### connect and send request line-by-line
```bash
netcat -C <url> -p <port>
```
##### send get and post field in 1 request

```bash
curl -X POST "example.site/test?get_data=56" -d "post_data=78"
```

##### generate and send some dummy cookies
```bash
dummy_cookies=$(for i in {1..100}; do echo -n "cookie$i=value$i; "; done)
curl -X POST "https://intro.spbctf.com/cookie2/" -b "$dummy_cookies"
```
