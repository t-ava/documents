# Clone & Install packages
```
git clone https://github.com/t-ava/tava-frontend.git
```

You need [nodeJS](https://nodejs.org/en/download/) and `npm`.

```
npm install
```

# Set Hardcoded Factors

### Set gecko node

in [`txs.js`](https://github.com/t-ava/tava-frontend/blob/66a17e550e5ca30b5047898738a95dd6d5a34314/frontend/public/js/txs.js#L15).

* For example: 
```javascript
const NODE = 'http://satoshi.snu.ac.kr:9650/ext/bc/X';
```

### Set DNN-server

in [`app.js`](https://github.com/t-ava/tava-frontend/blob/66a17e550e5ca30b5047898738a95dd6d5a34314/frontend/public/js/app.js#L17).

* For example: 
```javascript
const DNN_SERVER = 'http://satoshi.snu.ac.kr:8327/post';
```

# Run server
```
node server.js
```

Port number: 8084 as default.
