# Ethereum Token Manager

1. This is a token manager contract whose job is to provide (mint) and redeem (melt) tokens(ERC223) on demand.  
2. When the token manager mints and melts tokens, the contract will receive or pay out ethereum in compensation for the tokens.  
3. The contract will always mint/melt at a single exchange rate, specified in the contract's constructor.
4. Implemented another contract that is capable of holding tokens (named TokenHolder).

# Testing

Instantiated the classes tested moving tokens between holders and the market makers, and from one holder to another.

# Detailed Overview

1. Implemented a "TokenHolder" contract that derives from ITokenHolder.  
2. Implemented the TokenManager contract (located in tokenMgr.sol).  The TokenManager creates the token type, and mints and melts tokens on demand, at a defined exchange rate.  Its basically the market maker and provides an essentially infinite "pool" of tokens to draw from.  Therefore it is BOTH an ERC223Token and a TokenHolder.
3. Token sales occur in 2 steps.  The TokenHolder must first make some tokens available for sale by calling "putUpForSale".  Then the buyer can call the "sellToCaller" function (with the appropriate payment) and this function will transfer tokens from seller to buyer.
4.  To move tokens between 2 contracts without a sale (presumably owned by the same entity), implement the "withdraw" function.  Hint: This is a 1-liner.
5. Implemented "remit" which sells tokens back to the token manager.  
6. Included comprehensive tests to ensure expected behaviour and avoid leaks.
