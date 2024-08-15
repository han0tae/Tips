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


<pre>
<code>
          # check for lifetime liveness, restarts if dead
        livenessProbe:
          exec:
            command:
            - /bin/sh
            - -c
            - /usr/bin/chronyc dump | grep 200
          initialDelaySeconds: 5
          periodSeconds: 10

        # check for initial readiness
        readinessProbe:
          exec:
            command:
            - cat
            - /etc/chrony/chrony.conf
            #- /bin/sh
            #- -c
            #- /usr/bin/chronyc dumpc | grep 200
          initialDelaySeconds: 3
          periodSeconds: 3
</code>
</pre>
