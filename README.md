# loadbalancer
LoadBalancer using go

## Usage 
Example usage of LoadBalace
```
    servers := []Server{
		NewSimpleServer("https://www.google.com"),
		NewSimpleServer("https://www.bing.com"),
		NewSimpleServer("https://www.duckduckgo.com"),
	}

	lb := NewLoadBalancer("8000", servers)
	handleRedirect := func(rw http.ResponseWriter, req *http.Request) {
		lb.ServeProxy(rw, req)
	}

	// register a proxy handler to handle all requests
	http.HandleFunc("/", handleRedirect)

	fmt.Printf("serving requests at 'localhost:%s'\n", lb.port)
	http.ListenAndServe(":"+lb.port, nil)
```
