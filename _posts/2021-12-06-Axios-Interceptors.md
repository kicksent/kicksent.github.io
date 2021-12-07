# Axios Interceptors

## What are Interceptors?

They are a middleware that allows us to run some code before and/or after every request

Example problem:
Let's say we are making a request that requires a token with an expiration attached to it. Perhaps this is a user token and they click a link to look at an authenticated page after being away for a few minutes.

There are two solutions

1. Before making the original request, we can use our interceptor to check the expiration of the token. If it is expired then we can refresh the token using another request, and then once it is refreshed, then we will make our original request using the newly refreshed token. This ensures that our request will never fail due to having an expired token.

2. After making the request, if the request fails because the token is expired, we can use ourt interceptor to make a request to refresh the token, and then simply make the request again with this newly refreshed token. This means that sometimes our requests will fail but it's nearly the same result as solution #1

## Here's what the basic code sample looks like for interceptors

```
// Add a request interceptor
axios.interceptors.request.use(config => {
    // Do something before request is sent
    return config;
  }, error => {
    // Do something with request error
    return Promise.reject(error);
  });

// Add a response interceptor
axios.interceptors.response.use(response => {
    // Any status code that lie within the range of 2xx cause this function to trigger
    // Do something with response data
    return response;
  }, error => {
    // Any status codes that falls outside the range of 2xx cause this function to trigger
    // Do something with response error
    return Promise.reject(error);
  });
```

Now if you want to really implement this in a project and be able to test it. You want to create an instance of axios to use for making requests.

Here's what that looks like:

`const axiosInstance = axios.create()`

_Notes to myself:_
When I was implementing this I ran into an issue which was causing tests to break. If you are using this with nock you need to set the adapter(my particular issue, see below) to use http or it won't work.
There may also be CORS considerations which you can also configure in this object.

```
const axiosInstance = axios.create({
  // withCredentials: true,
  adapter: require('axios/lib/adapters/http'), //solved my issue
  headers: {
    //set cors stuff here or other header configurations
    //ex: 'Access-Control-Allow-Origin': '*'
    //ex: 'Access-Control-Allow-Methods':'GET,PUT,POST,DELETE,PATCH,OPTIONS',
  }
})
```

Then import/export this instance for use in test files, api calls, etc.

`export default axiosInstance`

(I placed my instance in a utils folder in my project)
`import axiosInstance from '../utils/axiosInstance'`

Be sure that in your file you update the interceptors to use this instance

`axios.interceptors.response.use...` becomes `axiosInstance.interceptors.response.use`

and

`await axios.get("example.com")` becomes `await axiosInstance.get("example.com")`
