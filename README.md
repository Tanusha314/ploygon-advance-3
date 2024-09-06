# ploygon-advance-3

## Overview

This project demonstrates the implementation of a zk-SNARK circuit using the **circom** programming language. The circuit proves knowledge of inputs A and B that satisfy specific logic gate outputs, with the final result verified on-chain using a Solidity smart contract.

## Circuit Description

The circuit implements a truth table-based logical gate, producing an output based on the following inputs:

| A  | B  | X  | Y  | Q  |
|----|----|----|----|----|
| 0  | 0  | 0  | 1  | 1  |
| 0  | 1  | 0  | 0  | 0  |
| 1  | 0  | 0  | 1  | 1  |
| 1  | 1  | 1  | 0  | 1  |

The goal is to prove knowledge of the inputs **A = 0** and **B = 1**, yielding the output `Q = 0`.

## Project Workflow

### Step 1: Circuit Implementation
- Write the circuit in **circom** following the desired logical gates.
- The circuit will be used to generate zk-SNARK proofs.

### Step 2: Compile the Circuit
- Compile the `circuit.circom` file to generate necessary intermediaries such as R1CS, witness, and keys.

### Step 3: Proof Generation
- Generate a zk-SNARK proof using inputs `A = 0` and `B = 1`.

### Step 4: Verifier Deployment
- Deploy a Solidity verifier smart contract to the **sepolia** or **amoy** Testnet. The verifier will be used to validate the zk-SNARK proof on-chain.

### Step 5: Verification of the Proof
- Call the `verifyProof()` method on the deployed verifier contract to verify the proof, and assert that the output is correct.

## Technical Steps

### Step 1: Install Dependencies

To get started, install the required packages:

```bash
npm install
```

### Step 2: Update Hardhat Configuration

Ensure that the `hardhat.config.js` file is correctly configured for your project, including network details for sepolia or amoy.

### Step 3: Compile the Contract

Compile the Solidity verifier contract:

```bash
npx hardhat compile
```

### Step 4: Deploy the Contract

Deploy the verifier contract using the following command:

```bash
npx hardhat run scripts/deploy.ts
```

### Step 5: Verify Deployment

After deploying the contract, verify that everything is working by calling the `verifyProof()` method. If successful, the terminal should print `"true"` indicating that the proof was correctly verified.

---

## Important Considerations

- **Security**: Use a `.env` file to securely store sensitive information like private keys. Ensure this file is excluded from version control.
- **Testing**: Thoroughly test your contract on a testnet before deploying to production to avoid costly errors.
- **Proof Verification**: Always validate proofs before deploying any zk-SNARK-based system on-chain to ensure correctness.

By following these steps, you'll implement a zk-SNARK-based circuit and successfully deploy its verifier contract on a public blockchain testnet.
