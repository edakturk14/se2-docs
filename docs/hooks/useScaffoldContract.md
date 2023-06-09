---
sidebar_position: 6
---

# useScaffoldContract

Use this hook to get your contract instance by providing the contract name. It enables you interact with your contract methods.
For reading data or sending transactions, it's recommended to use `useScaffoldContractRead` and `useScaffoldContractWrite`.

```ts
const { data: yourContract } = useScaffoldContract({
  contractName: "YourContract",
});
// Returns the greeting and can be called in any function, unlike useScaffoldContractRead
await yourContract?.greeting();

// Used to write to a contract and can be called in any function
import { Signer } from "ethers";
import { useSigner } from "wagmi";

const { data: signer, isError, isLoading } = useSigner();
const { data: yourContract } = useScaffoldContract({
  contractName: "YourContract",
  signerOrProvider: signer as Signer,
});
const setGreeting = async () => {
  // Call the method in any function
  await yourContract?.setGreeting("the greeting here");
};
```

This example uses the `useScaffoldContract` hook to obtain a contract instance for the `YourContract` smart contract. The data property of the returned object contains the contract instance that can be used to call any of the smart contract methods.
