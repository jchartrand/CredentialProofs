+++ Key validity

The key is the key:  It's all about the authenticity and validity of the issuing key.

ALWAYS NEED SOME ASSERTION, at the time of verification, THAT THE ISSUING KEY IS AUTHENTIC AND WAS VALID AT TIME OF ISSUANCE, i.e.
was being legitimately used within a period that encompasses the issuance of the given cred, and wasn't subsequently revoked for that period.
So this could be a date range for the key, as simple as list of pairs like:

PublicKey.      Valid Range.
98798798        2020-01-24Z13:00 - 2020-01-24Z14:00 

which would indicate the key was valid for a one hour period on January 24th.
If a credential claims to have been signed by this key outside that range, it isn't valid.

A list like this relies on an indendently verifiable timestamp.

Critically, this list has to be trustworthy, so we have to find the list somewhere we trust, like a web site, an app.  Without
this trustworthy list, the timestamp provided by the blockchain (or other) is useless.

So, given we need the revocation list which has to be maintained indefnitely (even if the list is itself on a blockchain,
we still need to maintain a set of pointers to the list), then why not just directly maintain a list of valid certs?  The list
could be a key store with hash of the cert, or merkle hash.

Basically do same thing as we do with blockchain, but instead store in our store so we can:
- permanently delete certs when we want to
- revoke when we want to (perhaps by having one 'valid' list and one 'revoked' list)
- don't need timestamp anymore since the cert won't appear in list unless valid.  

IT FUNDAMENTALLY COMES DOWN TO MAINTAINING NOT JUST A 'NEGATIVE' LIST, I.E, OF REVOCATIONS (OF EITHER CERTS OR ISSUING KEYS)
BUT ALSO A 'POSITIVE' LIST.   AND SINCE WE ALWAYS NEED THE NEGATIVE LIST THE ONLY DOWNSIDE TO THE POSITIVE LIST IS EXTRA STORAGE.
BUT THE UPSIDE IS THAT BECAUSE WE CONTROL THAT STORAGE, WE CAN DELETE HASHES (WHICH WE WOULD OTHERWISE HAVE PUT IN BLOCKCHAIN).

IT IS THAT WE RECORD POSITIVE CERTS INDIRECTLY IN A BLOCKCHAIN, USING TIMESTAMP AND KEY LIST.  BUT WITH NO REAL GAIN BECAUSE
WE ALWAYS NEED THE CORRESPONDING NEGATIVE LIST.

One argument is monitoring.  If we have a central list, then any access to the list can be monitored.  But, would it really show
anything meaninful, if people take copies of the list, and find the entry in which they are interested themselves?  

+++ Permanent secure versioning of updatable revocation list
