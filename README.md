# BUcry (Bitcoin Unlimited CRasher in RubY)
Ruby script to remotely crash Bitcoin Unlimited XTHIN nodes by sending an invalid GET_XTHIN request.

Vulnerability was responsibly disclosed prior to tool release.

The vulnerable code in question is:

```C++
else if (inv.type == MSG_THINBLOCK)
{
    //irrelevant
} else {
    assert(0); //instead of banning us for using an invald GET_XTHIN, the node trusts our request. 
    
    Blindy trusting newtwork data is a Bad Thing™.
```
Excerpt of https://github.com/BitcoinUnlimited/BitcoinUnlimited/blob/release/src/thinblock.h

As of 17:00 on /14/03/17, an update to patch the vulnerability has been pushed to the network and the nodes are slowly updating to the new code.
