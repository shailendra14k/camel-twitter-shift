oc apply -f servicefile.yml

[cpandey@cpandey camel-twitter-shift]$ oc get svc

NAME           TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE

demo-service   ClusterIP   172.30.86.125   <none>        9956/TCP   9m

oc expose service demo-service

[cpandey@cpandey camel-twitter-shift]$ oc get route

NAME           HOST/PORT                                                   PATH      SERVICES       PORT            TERMINATION   WILDCARD

demo-service   demo-service-imc-demo.apps.csppnq.lab.pnq2.cee.redhat.com             demo-service   undertow-port                 None

[cpandey@cpandey camel-twitter-shift]$ 

curl -v http://demo-service-imc-demo.apps.csppnq.lab.pnq2.cee.redhat.com/undertowTest



[cpandey@cpandey camel-twitter-shift]$ oc autoscale dc/fuse74-camel-twitter --min 1 --max 5 --cpu-percent=3
horizontalpodautoscaler.autoscaling/fuse74-camel-twitter autoscaled

[cpandey@cpandey camel-twitter-shift]$ oc get hpa
NAME                   REFERENCE                               TARGETS        MINPODS   MAXPODS   REPLICAS   AGE
fuse74-camel-twitter   DeploymentConfig/fuse74-camel-twitter   <unknown>/3%   1         5         0          4s
[cpandey@cpandey camel-twitter-shift]$ 


[cpandey@cpandey camel-twitter-shift]$ oc delete hpa fuse74-camel-twitter
horizontalpodautoscaler.autoscaling "fuse74-camel-twitter" deleted

