Penulis: [luthfi0x](https://www.twitter.com/luthfi0x)

# Pengenalan
Bab ini berisi pengenalan mengenai Eclipse

## Eclipse
> [!NOTE]
> Eclipse adalah sebuah ETH L2 yang menggunakan Solana sebagai execution layer dan Ethereum sebagai settlement layer

### Investor
![image](https://github.com/ZuperHunt/Eclipse-Testnet/assets/33769324/173b8277-91c0-43d9-ba8b-cf9a0622a0b3)

# Tutorial Deploy Smart Contract
Bab ini berisi tutorial cara mendeploy smart contract ke Eclipse testnet

## Requirement
- Gitpod
- 0.1 Sepolia ETH
  
## Dependencies

### Install Rust dan Cargo
```
mkdir -p /home/gitpod/.config/fish/conf.d/
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
chmod +x /workspace/.cargo/env
/workspace/.cargo/env
```

### Install Solana
```
sh -c "$(curl -sSfL https://release.solana.com/stable/install)
```

### Setting Solana to Eclipse Testnet
```
solana config set --url https://testnet.dev2.eclipsenetwork.xyz
```

### Membuat Wallet Solana
```
solana-keygen new
```
> [!CAUTION]
> Simpan PK yang dihasilkan!

## Bridge Sepolia ETH to Solana

### Install Yarn

```
npm install -g yarn
```

### Download Program
```
git clone https://github.com/Eclipse-Laboratories-Inc/testnet-deposit && cd testnet-deposit
yarn install
```

### Bridge Fund

```
node deposit.js [Address_SOL_YANG_UDAH_DIBUAT] 0x7C9e161ebe55000a3220F972058Fb83273653a6e 15000000 100 [PK_WALLET_YANG_BERISI_SEPOLIA_ETH] https://rpc.sepolia.org
```

## Deploy Smart Contract

### Dwonload Program
```
git clone https://github.com/solana-labs/example-helloworld
cd example-helloworld
npm install
```

### Build dan deploy SC-nya
```
npm run build:program-rust
```
```
solana program deploy dist/program/helloworld.so
```
```
npm run start
```
Pastikan hasilnya seperti
```
Let's say hello to a Solana account...
Connection to cluster established: http://127.0.0.1:8899 { 'feature-set': 2045430982, 'solana-core': '1.7.8' }
Using account AiT1QgeYaK86Lf9kudqKthQPCWwpG8vFA1bAAioBoF4X containing 0.00141872 SOL to pay for fees
Using program Dro9uk45fxMcKWGb1eWALujbTssh6DW8mb4x8x3Eq5h6
Creating account 8MBmHtJvxpKdYhdw6yPpedp6X6y2U9dCpdYaZJdmwV3A to say hello to
Saying hello to 8MBmHtJvxpKdYhdw6yPpedp6X6y2U9dCpdYaZJdmwV3A
8MBmHtJvxpKdYhdw6yPpedp6X6y2U9dCpdYaZJdmwV3A has been greeted 1 times
Success
```
Copy `8MBmHtJvxpKdYhdw6yPpedp6X6y2U9dCpdYaZJdmwV3A` dan submit di [form ini](https://forms.gle/yJfFABQDPmpvgzAf7)

## Help

Join komunitas [Discord ZuperHunt](https://t.co/n7TeWVlA48) jika kamu ada pertanyaan.

## Change Logs

* 0.0.1
    * Initial Release
