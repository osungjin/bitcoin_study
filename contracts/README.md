
# Run docker
`docker run --name eosio \
  --publish 7777:7777 \
  --publish 127.0.0.1:5555:5555 \
  --volume CONTRACTS_DIR:/Users/lineplus/Project/bitcoin_study/contracts \
  --detach \
  eosio/eos:v1.4.2 \
  /bin/bash -c \
  "keosd --http-server-address=0.0.0.0:5555 & exec nodeos -e -p eosio --plugin eosio::producer_plugin --plugin eosio::chain_api_plugin --plugin eosio::history_plugin --plugin eosio::history_api_plugin --plugin eosio::http_plugin -d /mnt/dev/data --config-dir /mnt/dev/config --http-server-address=0.0.0.0:7777 --access-control-allow-origin=* --contracts-console --http-validate-host=false --filter-on='*'"`


- EOS
  - tutorial
    - https://developers.eos.io/eosio-home/docs
    - password : PW5J6HwjHLQZXBrbYdcmR3kbk6g9g5XZnGkaprz8h1J6KAcr9w2jC
    - development private key : 5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3

    - create contract
      - cleos set contract hello2 ./contracts/hello hello.wasm hello.abi -p hello2@active
    - Action 실행
      - cleos push action hello2 hi '["user1"]' -p hello2

    - Token 생성
      - https://medium.com/hexlant/eos-token-%EC%83%9D%EC%84%B1%EA%B3%BC-%EB%B0%9C%ED%96%89-%EC%A0%84%EC%86%A1-20a5aa1cafbc
      - cleos push action hello2 create '["hello2", "10000000000.0000 HEX"]' -p hello2

    - 확장자
        - wasm : 텍스트 파일로써 읽을 수 있는 webAssembly 파일
        - wast : 컴퓨터가 실제로 이해할 수 있는 webAssembly 파일
        - abi : JSON과 Binary 간에 사용자 작업을 변환하는 방법에 대해 설명해주는 파일입니다
