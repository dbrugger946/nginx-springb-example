# ngx-example


Article this is pulled from  
https://medium.com/@haozhao_2156/an-effective-way-of-serving-static-content-and-a-reverse-proxy-gateway-with-nginx-on-openshift-214921dfbbc8


Need to first deploy the example SpringBoot App
https://github.com/jaysonzhao/springboot-openshift

```
oc new-build openshift/nginx~https://github.com/dbrugger946/ngx-example.git \
  --name=nginxbase \
  --strategy=source
```

```
oc new-app https://github.com/dbrugger946/ngx-example.git \
  --context-dir=conf \
  --strategy=docker \
  --name=reverse-proxy
oc expose svc/reverse-proxy
```
