# Diffie-Hellman Key Exchange in Go

This project demonstrates a simple **Diffie-Hellman key exchange** implementation in Go, with a client and server communicating over TCP. The shared secret generated can be used for symmetric encryption.

---

## Project Structure

- `client/main.go` – Connects to the server, sends its public key, and computes the shared key.
- `server/main.go` – Listens on a TCP port, receives the client's public key, sends its own, and computes the shared key.

---

## How It Works

1. Both client and server generate a **private key** (random number modulo `p`).
2. They generate a **public key**:  
   $publicKey = g^{privateKey} \mod p$
3. The client sends its public key to the server.
4. The server sends its public key back.
5. Both compute the **shared secret**:
   $sharedKey = (otherPartyPublicKey)^{privateKey} \mod p$
6. Both sides now have the same shared key without transmitting it directly.

---

## RFC MODP 2048

The code uses the **RFC 3526 2048-bit MODP Group** prime (`p`) and generator (`g = 2`) for key generation.

---

## Running the Project

1. Start the server:
```bash
go run ./server/main.go

```


2. Start the client:
```bash
go run ./client/main.go

```


