Kubernetes ETCD cluster. 

Yaml file creates:
  1. Headless service. 
  2. Headed service.
  3. Statefulset. (Pods with replica)

User can use headed service or headless service which ever is needed. The data is persistsent over restart of pod, or complete cluster or cluster goes in unhealthy mode because qorun [(n-1)/2] members are lost.

Cluster implementation -
  - Initially cluster will create a new cluster. 
  - If cluster goes into an unhealthy state, etcd cluster will come up and retain the data.
  - If the host is restarted, etcd cluster will come up and will retain the data.
  - If user cleans up the cluster and starts again, the data is persisted. 

NOTE: It is users responsibility to explicitly delete the data directory ("/data/etcd") whenever they don't want to persist the data.
