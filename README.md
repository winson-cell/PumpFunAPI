# Welcome to PumpClown, API for Pump.fun token

API for pump.fun

## No RPC No Problem

We provide RPC for you, so that the transaction is faster, and better

## Buy Token

```
import fetch from "node-fetch";

const url = 'https://pumpclown.zeabur.app/transaction/Buy';
const data = {
    mintAddress: "14uNeiwwemx6iEDcNfHrmdLuM6p3bTNzABaGjPggfuCk", // token address
    amount: 0.01, // In solana
    slippageDecimal: 0.02, // Slippage in percentage, 0.02 mean 2% slippage
    priorityFee: 0.1, // by default it uses 0.000005 solana per transaction, if set to 0.1 then total transaction would be 0.000005 + 0.1 solana
    secretKeypair: "xxx"
};

fetch(url, {
    method: 'POST', // Specify the request method
    headers: {
        'Content-Type': 'application/json' // Set the content type to JSON
    },
    body: JSON.stringify(data) // Convert the data to a JSON string
})
    .then(response => {
        if (!response.ok) {
            // Handle HTTP errors
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        // Check if the response is JSON
        const contentType = response.headers.get('content-type');
        if (contentType && contentType.includes('application/json')) {
            return response.json(); // Parse JSON response
        } else {
            return response.text(); // Parse text response
        }
    })
    .then(responseData => {
        console.log('Success:', responseData); // Log the response data
    })
    .catch(error => {
        console.error('Error:', error); // Log any errors
    });
```

## Sell Token

```
import fetch from "node-fetch";

const url = 'https://pumpclown.zeabur.app/transaction/Sell';
const data = {
    mintAddress: "14uNeiwwemx6iEDcNfHrmdLuM6p3bTNzABaGjPggfuCk", // token address
    sellPercent: 100, // In percentage 100 means 100%
    slippageDecimal: 0.02, // Slippage in percentage, 0.02 mean 2% slippage
    priorityFee: 0.1, // by default it uses 0.000005 solana per transaction, if set to 0.1 then total transaction would be 0.000005 + 0.1 solana
    secretKeypair: "xxx"
};

fetch(url, {
    method: 'POST', // Specify the request method
    headers: {
        'Content-Type': 'application/json' // Set the content type to JSON
    },
    body: JSON.stringify(data) // Convert the data to a JSON string
})
    .then(response => {
        if (!response.ok) {
            // Handle HTTP errors
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        // Check if the response is JSON
        const contentType = response.headers.get('content-type');
        if (contentType && contentType.includes('application/json')) {
            return response.json(); // Parse JSON response
        } else {
            return response.text(); // Parse text response
        }
    })
    .then(responseData => {
        console.log('Success:', responseData); // Log the response data
    })
    .catch(error => {
        console.error('Error:', error); // Log any errors
    });
```
## Fee
Every transaction will cost 0.25% of fee
