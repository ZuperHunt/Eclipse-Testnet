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

## 1. Requirements
- [Gitpod](https://www.notion.so/luthfi0x/a0d4305fcce84d0da856f3d58765eaf1?v=288fd59d31ae4295ac44a566bf971649&p=a82c45e276ea436986959e83d26b32f8&pm=c)
- 0.1 Sepolia ETH
  
## 2. Dependencies

### 2.1 Install Rust dan Cargo
```
mkdir -p /home/gitpod/.config/fish/conf.d/
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
chmod +x /workspace/.cargo/env
/workspace/.cargo/env
```

### 2.2 Install Solana
```
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
```

### 2.3 Install `spl-token-cli`
```
cargo install spl-token-cli
```

### 2.4 Setting Solana to Eclipse Testnet
```
solana config set --url https://testnet.dev2.eclipsenetwork.xyz
```

### 2.5 Membuat Wallet Solana
```
solana-keygen new
```
> [!CAUTION]
> Simpan PK yang dihasilkan!

## 3. Bridge Sepolia ETH to Solana

### 3.1 Install Yarn

```
npm install -g yarn
```

### 3.2 Download Program
```
git clone https://github.com/Eclipse-Laboratories-Inc/testnet-deposit && cd testnet-deposit
yarn install
```

### 3.3 Bridge Fund

```
node deposit.js [Address_SOL_YANG_UDAH_DIBUAT] 0x7C9e161ebe55000a3220F972058Fb83273653a6e 15000000 100 [PK_WALLET_YANG_BERISI_SEPOLIA_ETH] https://rpc.sepolia.org
```

## 4 Deploy Smart Contract

### 4.1 Dwonload Program
```
git clone https://github.com/solana-labs/example-helloworld
cd example-helloworld
npm install
```

### 4.2 Build dan deploy SC-nya
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

## 5. Buat Token

Buat token SPL:
```
spl-token create-token
```
Copy `token address` dari output menjalankan perintah di atas.

### 5.1 Buat Akun Kosong
Ini diperlukan untuk nampung token yang udah dibuat sebelumnya, ubah `YOUR_TOKEN_ADDRESS` sesuai punyamu yang udah dicopy tadi.
```
spl-token create-account YOUR_TOKEN_ADDRESS
```
Setelah menjalankan command di atas, akan muncul `wallet address` baru.

### 5.2 Mint Token
Ubah `YOUR_TOKEN_ADDRESS` sesuai punyamu
```
spl-token mint YOUR_TOKEN_ADDRESS 10000
```

### 5.3 Kirim Token
Kirim token tersebut ke wallet yang sebelumnya sudah dibuat di `subbab 2.5`.
```
spl-token transfer YOUR_TOKEN ADDRESS 50 YOUR_WALLET_ADDRESS
```

## Help

Join komunitas [Discord ZuperHunt](https://t.co/n7TeWVlA48) jika kamu ada pertanyaan.

## Change Logs

* 0.0.1
    * Initial Release
