### Nodejs + Docker + Kubernetes

### Prerequisite 
 - Docker
 - Kubernetes
 - Skaffold

Add below for load balanacing : 
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/cloud/deploy.yaml
```

#### Generate the common secret key
```
kubectl create secret generic jwt-secret --from-literal=JWT_KEY=asdf
```

#### command to run 
```
skaffold dev
```

#### Postman code for api calling
```
var request = require('request');
var options = {
  'method': 'POST',
  'url': 'https://ticketing.dev/api/users/signup',
  'headers': {
    'Content-Type': 'application/json',
    'Cookie': 'express:sess=eyJqd3QiOiJleUpoYkdjaU9pSklVekkxTmlJc0luUjVjQ0k2SWtwWFZDSjkuZXlKcFpDSTZJalZtTURVNFkyTm1ORGM1TnpjNE1EQXhPRFV5WWpCa05DSXNJbVZ0WVdsc0lqb2ljMkZ0UUdWNFlXMXdiR1V1WTI5dElpd2lhV0YwSWpveE5UazBNVGs1TWpRM2ZRLkw1Y3ZoMTY1N0ZMVENSNVZOaU55YTlVWm1na3RBcHVnbXUzUnM5MGNSckkifQ=='
  },
  body: JSON.stringify({"email":"sam@example.com","password":"password"})

};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```