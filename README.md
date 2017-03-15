# BUCR
Remotely crash Bitcoin Unlimited XTHIN nodes by sending an invalid GET_XTHIN request.

The vulnerable code in question is present in thinblock.cpp:

```C++
else if (inv.type == MSG_THINBLOCK)
{
    //irrelevant
} else {
    assert(0); //instead of banning us for using an invald GET_XTHIN, the node trusts our request.
}
```
As of 14/03/17, an update to patch the vulnerability has been pushed to the network and the nodes are slowly updating to the new code.
