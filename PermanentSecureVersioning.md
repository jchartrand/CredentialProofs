###Permanent secure versioning

It may not be immediately obvious, but blockchains like Bitcoin provide a way to permanently store versionable content, where each version is immutable and the chain of versions is secure.

Each version is connected by transferring (spending) unspent money from the bitcoin transaction in which the latest version of the data is stored, to the transaction where the new version of the data will be stored.  We can then subsequently follow the trail of versions by following this trail of transfers. 

This can be useful for things like maintaining a public revocation list.

Downsides are:

- that we don't control the blockchain and so depend on the permanence of the blockchain.  
- We also depend on this subversion (storing non-financial data in the transaction) of the blockchain continuing to be available.  Given that it isn't the primary purpose of the blockchain, and certainly not one that makes any money for anyone, there are no guarantees that it will remain a viable system.
- We can't ever delete the data, possibly causing problems with privacy laws like GDPR
- Further, and perhaps most importantly, even with the data stored in the blockchain, we still have to store **trusted** pointers into the blockchain, i.e., we have to store the bitcoin transaction at the root of the list, which therefore amounts to storing another list, and this list has to be at a **trusted location**.  Given this, why not just store the revocation list directly at the trusted location.
