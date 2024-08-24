<pre><code>
apiVersion: v1
kind: Service
metadata:
  name: svc1
  namespace: default
spec:
  type: ExternalName
  externalName: svc1.external.com  
</code></pre>
