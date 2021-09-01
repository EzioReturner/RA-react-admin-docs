# Http Request

RA provides HTTP request services using AXIos, on which RA encapsulates, The file is located in `src/utlis/io.ts`[![](/media/link.svg)](https://github.com/EzioReturner/RATurbo-react-admin/blob/master/src/utils/io.ts)。

## Params standard
We agreed `params` param in request will parsing as http request query, and `data` will parsing as http request body content。

For example:
```javascript
export default function getWeather() {
  return io.get('https://restapi.amap.com/v3/weather/weatherInfo', {
    params: {
      key: 'cc24ccab0a88c3ee17eb8dee0e07ba61',
      city: 350200,
      extensions: 'all'
    }
  });
  // will parsing https://restapi.amap.com/v3/weather/weatherInfo?key=cc24ccab0a88c3ee17eb8dee0e07ba61&city=350200&extensions=all
}

export function postLogin(userName, password) {
  return io.post('/post/login', {
    data: {
      userName,
      password
    }
  });
}
```

## Custom Header 
You can modify the Header manually by calling the 'setHeader' method
```javascript
setHeader = (key, val) => {
  this.instance.defaults.headers.common[key] = val;
};
```
> For example, we set the cache policy to no cache in the header no-cache

```javascript
import io from '@utlis/io';
function getSome() {
  io.setHeader('Cache-Control', 'no-cache');
  return io.get('/get/wordCloud');
}
```

> It is important to note that calling the setHeader method changes the header configuration of the request instance globally, so we recommend configuring the interface separately

```javascript
export default function getWordCloud() {
  return io.get('/get/wordCloud', {
    options: {
      headers: {
        'Cache-Control': 'no-cache'
      }
    }
  });
}
```

Options See AxiosRequestConfig for the received parameter types [![](/media/link.svg)](https://github.com/axios/axios/blob/master/index.d.ts)

## The Interceptor

The IO tool provides a method to interceptors that can be configured for different interfaces.

```javascript
this.instance.interceptors.request.use(
  config => {
    {do something}
    return config;
  },
  error => {
    Promise.reject(error);
  }
);
```

## Exception

The IO tool provides methods for handling interface request exceptions. It handles different status codes for restful interfaces.

```javascript
handleError = error => {
  const { message, status } = error;
  switch (status) {
    case 401:
      {do something}
      break;
    case 404:
      {do something}
      break;
    case 500:
      {do something}
      break;
    default:
      this.notify(message || error);
      break;
  }
  return Promise.reject(error);
};
```