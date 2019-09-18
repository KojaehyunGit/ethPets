# PETS
* **이더리움 기반 펫 용품 거래 및 소통, 기부모금 웹페이지**
* 동물과 소셜네트워크서비스를 결합한 단어(PET + SNS)


## Team
* 권달형
* 고재현
* 김민선
* 김희재
* 문영선


## Background
> 1인 가구, 저출산·고령화 현상으로 매년 **반려동물**을 키우는 가구수가 늘어나면서 <br>
관련시장 규모가 엄청나게 커지고 있습니다. 최근에는 반려동물을 뜻하는 '펫(Pet)'과 <br>
가족을 의미하는 '패밀리(Family)'가 합쳐진 '**펫팸족**', 반려동물 관련시장 성장세를 반영한 <br>
'**펫코노미**(Pet+Economy)'라는 신조어까지 등장할 정도로 반려동물에 대한 관심도가 높아지고 있는 추세입니다. <br><br>
저희팀은 이러한 반려동물이라는 공감대를 **이더리움 기반**의 **블록체인 시스템**과 결합하여, <br>
참여할수록 보상받는 **인센티브 생테계 시스템** 형식의 **DAPP**으로 구현 하려고 합니다.


## Prerequisites
* Ubuntu - 16.04
* Solidity - ^0.5.1
* Node js - latest
* Express - latest
* Javascript
* Web3
* mongoDB - latest
* Socket.io - latest
* Git client - latest


## Solidity function: addPet(struct), transfer(ERC20_token)
```solidity
/* 동물등록 */
function addPet (uint256 _petage, string memory _breed, string memory _gender, string memory _location) public {
    pets.push(myStruct(_petage, _breed, _gender, _location, block.timestamp));
    emit pet(_petage, _breed, _gender, _location, block.timestamp);
  }
```

```solidity
/* 용품거래 */
function transfer(address to, uint256 value) public returns (bool) {
    _transfer(msg.sender, to, value);
    return true;
  }
```

## Web3.js: Metamask connect & transfer(Ether)
```javascript
/* 메타마스크 연동 */
window.addEventListener('load', function() {
    // Load WEB3
    // Check wether it's already injected by something else (like Metamask or Parity Chrome plugin)
    if(typeof web3 !== 'undefined') {
        web3 = new Web3(web3.currentProvider);
        //console.log("metaAddress")
    // Or connect to a node
    }
    // Check the connection
    if(!web3.isConnected()) {
        console.error("Not connected");
    }
   
/* 이더전송 */
    var accounts = ethereum.enable()
    .then( function(account) {
        //console.log(account);
        var accountInterval = setInterval(async function() {
            if (web3.eth.accounts[0] !== account) {
                account = web3.eth.accounts[0];
                console.log(account);
                document.getElementById("address").value = account;
                web3.eth.getBalance(account, function(err, result) {
                    balance = web3.fromWei(result, 'ether');
                    console.log(balance);
                    document.getElementById("balance").value = balance;
                })
            }
        }, 100);
    });
    
});
```
<br>


## Installing
### 1. 파일을 클론합니다.
```
git clone https://github.com/KojaehyunGit/ethPets.git
```

### 2. 필요한 NPM을 설치합니다.
```
npm install
```

### 3. 서버를 실행합니다.
```
node server.js
```

### 4. 브라우저에서 해당 포트로 접속합니다.
```
http://101.101.166.164:8080/
```
<br>


## Application Scenario

![image](https://user-images.githubusercontent.com/51254582/64399945-4d812000-d0a5-11e9-8d65-247ab00085bb.png)

![image](https://user-images.githubusercontent.com/51254582/64399951-540f9780-d0a5-11e9-8446-e5b62506254a.png)

![image](https://user-images.githubusercontent.com/51254582/64399958-5a057880-d0a5-11e9-9aa5-9c21a0ecd3fd.png)

![image](https://user-images.githubusercontent.com/51254582/64399994-76091a00-d0a5-11e9-95be-72e3a5070310.png)

![image](https://user-images.githubusercontent.com/51254582/64400000-7b666480-d0a5-11e9-87dd-1cfb3c30ea3d.png)

![image](https://user-images.githubusercontent.com/51254582/64400006-88835380-d0a5-11e9-9448-9510de2eec75.png)

![image](https://user-images.githubusercontent.com/51254582/64400152-1e1ee300-d0a6-11e9-9cd5-446c34a546ce.png)

![image](https://user-images.githubusercontent.com/51254582/64400018-9933c980-d0a5-11e9-9202-ff227b81cef8.png)

![image](https://user-images.githubusercontent.com/51254582/64400024-9e911400-d0a5-11e9-92fd-09cf1ddae9c1.png)

![image](https://user-images.githubusercontent.com/51254582/64400033-a5b82200-d0a5-11e9-9d4e-2f69580ea2e4.png)

![image](https://user-images.githubusercontent.com/51254582/64400037-a9e43f80-d0a5-11e9-8d6d-2dbbab7728a8.png)


## References
* Express - http://www.blueb.co.kr/?c=2/31&uid=4138
* Socket.io - https://codevkr.tistory.com/58?category=719250
