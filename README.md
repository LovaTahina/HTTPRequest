# HTTPRequest

HTTPRequest is a single-header library for making HTTP requests. You can just include it in your project and use it.

Usage:
```cpp
#include "HTTPRequest.hpp"

try
{
    http::Request request("http://test.com/test");

    // send a get request
    http::Response response = request.send("GET");
    std::cout << response.body.data() << std::endl; // print the result

    // send a post request
    response = request.send("POST", "foo=1&bar=baz", {
        "Content-Type: application/x-www-form-urlencoded"
    });
    std::cout << response.body.data() << std::endl; // print the result

    // pass parameters as a map
    std::map<std::string, std::string> parameters = {{"foo", "1"}, {"bar", "baz"}};
    response = request.send("POST", parameters, {
        "Content-Type: application/x-www-form-urlencoded"
    });
    std::cout << response.body.data() << std::endl; // print the result
}
catch (const std::exception& e)
{
    std::cerr << "Request failed, error: " << e.what() << std::endl;
}
```

## License

HTTPRequest codebase is licensed under the BSD license. Please refer to the LICENSE file for detailed information.
