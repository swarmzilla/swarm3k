Here's the special configuration to override the default Swarm configuration.
```json
{
  "ListenAddr": "0.0.0.0:2377",
  "AdvertiseAddr": "67.205.160.45:2377",
  "ForceNewCluster": true,
  "Spec": {
    "Orchestration": {},
    "Raft": { "KeepOldSnapshots": 1000000 },
    "Dispatcher": {},
    "CAConfig": {}
  }
}
```
It initializes Docker swarm and tell to keep all snapshots up to 1M entries.

`cat init_config | curl -XPOST --unix-socket /var/run/docker.sock -H "Content-Type: application/json" -d @- http:/swarm/init`
