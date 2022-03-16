# Klaytn Bapp example
인프런 강의(Klaytn 클레이튼 블록체인 어플리케이션 만들기 - 이론과 실습)에서 사용한 예제 코드(https://github.com/kkagill/addition-game-starter.git) 참고

- [node.js](https://nodejs.org) 10.16.0 버전 설치

- truffle 설치
    
    ```bash
    sudo npm uninstall -g truffle
    sudo npm install -g truffle@4.1.15
    truffle version
    ```

- 예제코드 클론 & npm install
    
    ```bash
    git clone https://github.com/ghkdgh2365/klaytn-bapp-example.git
    npm install
    ```

- Klaytn account private key 입력

    ```jsx
    // truffle.js 
    const PrivateKeyConnector = require('connect-privkey-to-provider')
    const NETWORK_ID = '1001'
    const GASLIMIT = '2000000'
    const URL = 'https://api.baobab.klaytn.net:8651'
    const PRIVATE_KEY = '' // 자신의 key로 수정

    module.exports = {
        networks: {
            klaytn: {
                provider: new PrivateKeyConnector(PRIVATE_KEY, URL),
                network_id: NETWORK_ID,
                gas: GASLIMIT,
                gasPrice: null,
            }
        },
    }
    ```

- 배포
    
    ```bash
    truffle deploy --network klaytn
    ```
    
- 컨트랙트 재배포
    
    ```bash
    truffle deploy --compile-all --reset --network klaytn
    ```
    
- 배포 확인
    
    ```json
    // build/contracts/AdditionGame.json
    ...
    "networks": {
        "1001": {
          "events": {},
          "links": {},
          "address": "0xc2cda11de7e8272364372bda145e788d02dd9695",
          "transactionHash": "0xd473333c2b950fa469286213135368ede0c513a78cdb76ef9e732654cdaddd8a"
        }
    },
    ...
    ```
