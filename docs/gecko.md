# Install & Run Gecko

You can get Gecko client code for Tava at https://github.com/t-ava/gecko/tree/extendSendAPI.

```console
$ go get -v -d github.com/ava-labs/gecko/...
$ cd $GOPATH/src/github.com/ava-labs/gecko
```

Until the Pull Request is accepted, you must change one file: vms/avm/service.go
* described in https://github.com/ava-labs/gecko/pull/179

Also add your node's ID to StakerIDs at https://github.com/ava-labs/gecko/blob/7671cab97260ab2eebd8b29f98b23e219da25a20/genesis/config.go#L291

How to know your node's ID
```python
# using pyslopes
nodeID = admin.getNodeID(API_NODE_IP)
```

``` console
$ ./scripts/build.sh
$ ./build/ava --public-ip=127.0.0.1 --http-port=9650 --staking-port=9651 --db-dir=db/node1 --staking-tls-enabled=false --snow-sample-size=1 --snow-quorum-size=1 --network-id=local
```
