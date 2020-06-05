# Repository

https://github.com/t-ava/gecko

# Install & Run Gecko

You can get Gecko client code for Tava at https://github.com/t-ava/gecko/tree/extendSendAPI.

```console
$ go get -v -d github.com/ava-labs/gecko/...
$ cd $GOPATH/src/github.com/ava-labs/gecko
```

Until the Pull Request is accepted, you must change one file: vms/avm/service.go
* described in https://github.com/ava-labs/gecko/pull/179

``` console
$ ./scripts/build.sh
$ ./build/ava --public-ip=127.0.0.1 --http-port=9650 --staking-port=9651 --db-dir=db/node1 --staking-tls-enabled=false --snow-sample-size=1 --snow-quorum-size=1 --network-id=local
```

# Run Tava initialize script

After running the gecko node, you should run Tava initialize code at [`initTAVA.py`](https://github.com/t-ava/pyslopes/blob/master/sampleCodes/initTAVA.py).

See [Pyslopes](https://github.com/t-ava/pyslopes) for more details.

```console
$ git clone https://github.com/t-ava/pyslopes.git
$ cd sampleCodes
```

You must set these variables properly in `initTAVA.py` script.

```python
LIB_PATH = path to pyslopes codes
API_NODE_IP = the gecko node's IP address
```

```console
$ python3 initTAVA.py
```

Then, you will see logs like this.

```console
final result
host balance: [{'asset': 'AVA', 'balance': '30000'}]
user1 balance: [{'asset': 'AVA', 'balance': '20000'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '11'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '13'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '15'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '6'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '5'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '6'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '13'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '5'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '12'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '6'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '8'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '15'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '10'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '10'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '9'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '5'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '7'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '11'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '9'}]
station balance: [{'asset': 'pePewnxEaP82Yd7cgnWbGUYgoBjvUwurvhzCLJpqusievGsUN', 'balance': '9'}]
```
