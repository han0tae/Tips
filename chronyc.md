<pre>
<code>
livenessProbe:
  exec:
    command:
      - /bin/sh
      - -c
      - "chronyc tracking"
  initialDelaySeconds: 60
  timeoutSeconds: 5
  periodSeconds: 10
  failureThreshold: 3
</code>
</pre>
