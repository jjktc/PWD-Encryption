# PWD-Encryption
MP7 - A unique password locked multi-layer encryption immune to character analysis<br />
==================== GOAL ====================<br />
The goal was to create an encryption which was unique to the password and thus could only be broken by someone who knew the password, rather than knew the encryption method.

==================== TIME ====================<br />
Since every encrypted message can be different based on the message or the password, the brute force method of testing various inputs is nearly impossible since the attacker would have to not only test every possible message but also test every possible password. The number of possibilities that would have to be tested would scale at a rate of c27^(m+p) with m being the number of letters in the message and p being the number of letters in the password and c being the time it takes to encrypt one message. So with a ten letter password and assuming c = 1 second
|______|_____|______________|<br />
|	 m	 |	p	 |	time		   	|<br />
|______|_____|______________|<br />
|  1	 |	10 |	5.6 * 10^15	|<br />
|	 2	 |	10 |	1.5 * 10^17	|<br />
|	 3	 |	10 |	4.1 * 10^18	|<br />
|	 4	 |	10 |	1.1 * 10^20	|<br />
|	 5	 |	10 |	3.0 * 10^21	|<br />
|	 6	 |	10 |	8.0 * 10^22	|<br />
|	 7	 |	10 |	2.2 * 10^24	|<br />
|	 8	 |	10 |	5.8 * 10^25	|<br />
|	 9 	 |	10 |	1.6 * 10^27	|<br />
|	 10	 |	10 |	4.2 * 10^28 | --> 100 billion * the age of the universe<br />
|______|_____|______________|<br />
<br />
and that is only with 10 characters for a password, let alone something like 20...<br />

==================== METHOD ====================<br />
Step 1:	Generate a sequence number that is unique to the password. ie: "password" --> 071724150123020426111409211200181310200603051625082219

Step 2:	Generate key-value pairs using a proprietary algorithm which creates the connections based on the sequence number.

Step 3:	Apply a 1:1 swap of the keys and values which is a substitution cipher.

Step 4:	Analyze the distribution of characters in the encrypted message.

Step 5:	Automatically determine the appropriate way to neutralize the message ie: add filler characters that disrupt the message and prevent character analysis aka "the scrabble method" (coined by yours truly) aka Statistical Frequency Analysis which is commonly used to break substitution ciphers like the one we applied in step 3

Step 6:	Calculate the unique neutralizing numbers and insert into the message using a similarly encrypted tag.

Step 7:	(Optional) Apply the encryption on itself to further randomize as many times as you'd like since the encryption can self-apply recursively. In order to keep the scaling low, this only applies it once but overriding the public encrypt and decrypt methods allows as many times as necessary.

Decryption is accomplished by undoing each step in the reverse order.
