# Welcome to PumpClown, API for Pump.fun token

API for pump.fun

## No RPC No Problem

We provide RPC for you, so that the transaction is faster, and better

# Javascript(Node js)
## Buy Token

```
import fetch from "node-fetch";

const url = 'https://pumpclown.zeabur.app/transaction/Buy';
const data = {
    mintAddress: "14uNeiwwemx6iEDcNfHrmdLuM6p3bTNzABaGjPggfuCk", // token address
    amount: 0.01, // In solana
    slippageDecimal: 0.02, // Slippage in percentage, 0.02 mean 2% slippage
    priorityFee: 0, // by default it uses 0.000005 solana per transaction, if set to 0.1 then total transaction would be 0.000005 + 0.1 solana
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
    priorityFee: 0, // by default it uses 0.000005 solana per transaction, if set to 0.1 then total transaction would be 0.000005 + 0.1 solana
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

# Python

## Buy Token
```
import requests

url = 'https://pumpclown.zeabur.app/transaction/Buy'
data = {
    "mintAddress": "14uNeiwwemx6iEDcNfHrmdLuM6p3bTNzABaGjPggfuCk",
    "amount": 0.01, # In solana
    "slippageDecimal": 0.02, # Slippage in percentage, 0.02 mean 2% slippage
    "priorityFee": 0, # by default it uses 0.000005 solana per transaction, if set to 0.1 then total transaction would be 0.000005 + 0.1 solana
    "secretKeypair": "xxx"
}

try:
    response = requests.post(url, json=data)
    response.raise_for_status()  # Raise HTTPError for bad responses (4xx and 5xx)

    # Check if the response is JSON
    if response.headers.get('Content-Type') == 'application/json':
        response_data = response.json()
    else:
        response_data = response.text

    print('Success:', response_data)
except requests.exceptions.RequestException as e:
    print('Error:', e)

```

## Sell Token

```
import requests

url = 'https://pumpclown.zeabur.app/transaction/Sell'
data = {
    "mintAddress": "14uNeiwwemx6iEDcNfHrmdLuM6p3bTNzABaGjPggfuCk",
    "sellPercent" : 100, # In percentage 100 means 100%
    "slippageDecimal": 0.02, # Slippage in percentage, 0.02 mean 2% slippage
    "priorityFee": 0, # by default it uses 0.000005 solana per transaction, if set to 0.1 then total transaction would be 0.000005 + 0.1 solana
    "secretKeypair": "xxx"
}

try:
    response = requests.post(url, json=data)
    response.raise_for_status()  # Raise HTTPError for bad responses (4xx and 5xx)

    # Check if the response is JSON
    if response.headers.get('Content-Type') == 'application/json':
        response_data = response.json()
    else:
        response_data = response.text

    print('Success:', response_data)
except requests.exceptions.RequestException as e:
    print('Error:', e)
```

## Fee
Every transaction will cost 0.25% of fee of total transaction amount


