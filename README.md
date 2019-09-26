oc apply -f servicefile.yml
oc expose service demo-service

[cpandey@cpandey camel-twitter-shift]$ oc get route
NAME           HOST/PORT                                                   PATH      SERVICES       PORT            TERMINATION   WILDCARD
demo-service   demo-service-imc-demo.apps.csppnq.lab.pnq2.cee.redhat.com             demo-service   undertow-port                 None
[cpandey@cpandey camel-twitter-shift]$ 


curl -v http://demo-service-imc-demo.apps.csppnq.lab.pnq2.cee.redhat.com/undertowTest
