# redis-cluster
kubectl exec -it -n redis redis-cluster-0 -- redis-cli --cluster create --cluster-replicas 0 \
$(kubectl get pods -n redis -l app=redis-cluster -o jsonpath='{range.items[*]}{.status.podIP}:6379 ')

Join Cluster Redis

Cluster MEET ip port //in new nodes
for slot in {0..5461}; do redis-cli CLUSTER ADDSLOTS $slot > /dev/null; done; //in new nodes
cluster forget id
