# Documentation

All VVS pairs consist of two different tokens. CRO is not a native currency in VVS, and is represented only by WCRO in the pairs. 

The canonical WCRO address used by the VVS interface is `0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c`.

Results are cached for 5 minutes (or 300 seconds).

## [`/summary`](https://info.vvs.finance/api/summary)

Returns data for the top ~1000 VVS pairs, sorted by reserves. 

### Request

`GET https://info.vvs.finance/api/summary`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "0x..._0x...": {                  // CRC20 token addresses, joined by an underscore
      "price": "...",                 // price denominated in token1/token0
      "base_volume": "...",           // last 24h volume denominated in token0
      "quote_volume": "...",          // last 24h volume denominated in token1
      "liquidity": "...",             // liquidity denominated in USD
      "liquidity_CRO": "..."          // liquidity denominated in CRO
    },
    // ...
  }
}
```

## [`/tokens`](https://info.vvs.finance/api/tokens)

Returns the tokens in the top ~1000 pairs on VVS, sorted by reserves.

### Request

`GET https://info.vvs.finance/api/tokens`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "0x...": {                        // the address of the CRC20 token
      "name": "...",                  // not necessarily included for CRC20 tokens
      "symbol": "...",                // not necessarily included for CRC20 tokens
      "price": "...",                 // price denominated in USD
      "price_CRO": "...",             // price denominated in CRO
    },
    // ...
  }
}
```

## [`/tokens/0x...`](https://info.vvs.finance/api/tokens/0x0E09FaBB73Bd3Ade0a17ECC321fD13a19e81cE82)

Returns the token information, based on address.

### Request

`GET https://info.vvs.finance/api/tokens/0x0E09FaBB73Bd3Ade0a17ECC321fD13a19e81cE82`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "name": "...",                    // not necessarily included for CRC20 tokens
    "symbol": "...",                  // not necessarily included for CRC20 tokens
    "price": "...",                   // price denominated in USD
    "price_CRO": "...",               // price denominated in CRO
  }
}
```

## [`/pairs`](https://info.vvs.finance/api/pairs)

Returns data for the top ~1000 VVS pairs, sorted by reserves.

### Request

`GET https://info.vvs.finance/api/pairs`

### Response

```json5
{
  "updated_at": 1234567,              // UNIX timestamp
  "data": {
    "0x..._0x...": {                  // the asset ids of CRO and CRC20 tokens, joined by an underscore
      "pair_address": "0x...",        // pair address
      "base_name": "...",             // token0 name
      "base_symbol": "...",           // token0 symbol
      "base_address": "0x...",        // token0 address
      "quote_name": "...",            // token1 name
      "quote_symbol": "...",          // token1 symbol
      "quote_address": "0x...",       // token1 address
      "price": "...",                 // price denominated in token1/token0
      "base_volume": "...",           // volume denominated in token0
      "quote_volume": "...",          // volume denominated in token1
      "liquidity": "...",             // liquidity denominated in USD
      "liquidity_CRO": "..."          // liquidity denominated in CRO
    },
    // ...
  }
}
```
