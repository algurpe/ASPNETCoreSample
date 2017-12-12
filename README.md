#Net.Core 2 Console App  
**Net.Core 2 Console App** checking if `HTTPResponse.HasStarted` status, a useful hint to indicate if headers have been sent and/or the body has been written to.
### Warning
Do not call `next.Invoke` after the response has been sent to the client. Changes to `HttpResponse` after the response has started will throw an **exception**. 
For example, changes such as setting headers, status code, etc, will throw an exception. 
Writing to the response body after calling `next`:
- May cause a protocol violation. For example, writing more than the stated `content-length`.
- May corrupt the body format. For example, writing an HTML footer to a CSS file.