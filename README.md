# Sending Headers with cURL

[<img src="https://img.shields.io/static/v1?label=&message=Curl&color=brightgreen" />](https://github.com/topics/curl) [<img src="https://img.shields.io/static/v1?label=&message=Headers&color=important" />](https://github.com/topics/headers)

- [Send HTTP headers](#send-http-headers)
- [Send Custom HTTP Headers](#send-custom-http-headers)
- [Send Multiple Headers](#send-multiple-headers)
- [Get/Show HTTP Headers](#getshow-http-headers)
- [Advanced Tips for Working with cURL Headers](#advanced-tips-for-working-with-curl-headers)
- [FAQ](#faq)

In this guide, we will discuss how to send and receive HTTP headers using cURL, a versatile command-line tool fortransferring data with URL syntax.

## Send HTTP headers

HTTP headers consist of a name-value pair, separated by a colon (:). The name identifies the type of informationsent, while the value is the actual data sent.

Some of the most common HTTP headers include the User-Agent, Content-Type, Accept, and Cache-Control.

- Host: example.com
- user-agent: curl/7.87.0
- accept: */*

You can change the value of these headers when sending a request.

To send HTTP headers with cURL, you can use the -H or --header option followed by the header name and value in theformat "Header-Name: value". Here's an example:

```sh
curl -H "User-Agent: MyCustomUserAgent" http://httpbin.org/headers
```

In this example, we are sending a custom User-Agent header as "MyCustomUserAgent" when requesting the http://httpbin.org/headers page.

![Change the value of User-Agent](images/curl-useragent.png)

The page http://httpbin.org/headers is meant for testing headers and it returns a JSON with all the headers itfound in the request. Ignore the X-Amzn header that this site uses internally.

## Send Custom HTTP Headers

To send custom HTTP headers with cURL,use the -H option and provide the header name and value:

```sh
curl -H "Authorization: Bearer my-access-token" http://httpbin.org/headers
```

## Send Multiple Headers

To send multiple headers with cURL,you can use the -H option multiple times in the same command:

```sh
curl -H "User-Agent: MyCustomUserAgent" -H "Accept:application/json" http://httpbin.org/headers
```

## Get/Show HTTP Headers

To view the response headers from aweb server, you can use the **-I** or **--head** option with cURL:

```sh
curl -I http://httpbin.org/headers
curl --head http://httpbin.org/headers
```

You can also use the **-i** or **--include** option to show both the response headers and the content in theoutput. For example:

```sh
curl -i http://httpbin.org/headers
curl --include http://httpbin.org/headers
```

## Advanced Tips for Working with cURL Headers

### Sending empty headers

```sh
curl -H "User-Agent;" http://httpbin.org/headers
```

### Removing headers

```sh
curl -H "User-Agent:" http://httpbin.org/headers
```

![You can use a colon with no value to remove a header](images/delete-header.png)

### Verbose mode

If you want to see more detailed information about the request and response, including the headers sent and received, you can use the -v or --verbose option.

```sh
curl -v http://httpbin.org/headers
curl --verbose http://httpbin.org/headers
```

### Saving headers to a file

```sh
curl -D headers.txt -o content.txt http://httpbin.org/headers
```

## FAQ

### How do you add headers in cURL?

```sh
curl -H "User-Agent: MyCustomUserAgent" http://httpbin.org/headers
```

### Does cURL automatically addheaders?

Yes, cURL automatically adds standardheaders, such as User-Agent, Accept, and Host, based on the request type and other options. You can override or add custom headers using the -H command.

### How to check HTTP headers in cURL?

To check the HTTP headers in cURL, usethe -I or --head option to retrieve only the headers without the actualcontent. For example:

```sh
curl -I http://httpbin.org/headers
```

Alternatively, you can use the -i or--include option to show both the response headers and the content in theoutput. For example:

```sh
curl -i http://httpbin.org/headers
```

### How can I remove a default headerin cURL?

To remove a header that cURL adds bydefault, provide the header name followed by a colon without a value. Forexample, to remove the User-Agent header:

```sh
curl -H "User-Agent:" http://httpbin.org/headers
```

If you want to learn how to use cURLwith a proxy, [read this blog post](https://oxylabs.io/blog/curl-with-proxy).
