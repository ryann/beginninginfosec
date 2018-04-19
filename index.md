
# INFOSEC, A primer.

## Who am I?

Don't worry about it.

## First and foremost [Kanye](https://www.youtube.com/watch?v=l1lc0sHz2WI),

.. You are **going to get owned**. Accept it. Deal with it. Privacy is dead. You are not a snowflake.

You frankly just have too big of an attack surface. You probably have WIFI, accounts all over the place with what I hope aren't shared passwords. Passwords which are probably some iteration on a pet you once had, or a girl you once wanted to fuck. Maybe with a bang at the end, because it's [more secure that way](https://xkcd.com/936/). Your fridge probably has a fucking twitter app at this point. Have you disassembled and audited the firmware on your router? Your 'smart' scale? Especially that fucking dropcam outside, man. I sure as fuck haven't. 

Developers are human, they make mistakes.

It's not that they aren't trying. No developer starts his day wanting to eat shit because his trash code had a vulnerability that hit the reuters wires. He meant to get to it. It was a known issue. I swear it was marked '#TODO FIXME' in the code. These are human beings. Probably doing a job they don't like on not nearly enough hours of sleep.  Would you want to get up every day and go work for Symantec? No, of course not. They don't either.

### All developers write shitty code.

Writing secure code is hard. Ask [Paul Vixie](https://en.wikipedia.org/wiki/Paul_Vixie). He has a fucking helicopter. But that's neither here nor there. Vixie is the man responsible for BIND--the code that runs most of the worlds DNS servers--you know: the magic that resolves "pornhub.com" into "185.53.178.8". He also wrote crontab, a UNIX server scheduling daemon that's installed on all basically every sever in the world.

The guy is really a remarkable human being. Software engineer at DEC. He's a founding member of the ISC for fucks sake. My point is there was a period in the early aughts where his lifes work was getting abused left and right. Bored teenagers were the fuel, and a misisng bounds check was the fire. He wasn't a shitty developer. He was a great developer. He liked to build shit.  He didn't necessarily think **SECURITY FIRST**.

## Security First

It's a game of trade offs. Obviously in a perfect world all of your data would be both secure and available on demand. There are trade-offs to consider if you are storing 100BTC in a cold wallet. Do you print off QR codes? Where do you put the codes? What happens if a meteor hits California? What is an acceptable latency for you to be "liquid" ?

# Let's get to the point.

### Use a hardware wallet.

But never relegate physical access. All one has to do is look at the [ChangeLog](https://blog.trezor.io/trezor-firmware-security-update-1-5-2-5ef1b6f13fed) of your most pop
A hardware wallet can be thought of a second party in a 2 of 3 multi sig wallet.

Simply using a hardware wallet can stop an attacker with perfect information in his tracks.

### Learn how to use GPG.

It's simple. It's the cryptography behind everything. Public key encryption. It's [Pretty Good Privacy(PGP)](https://en.wikipedia.org/wiki/Pretty_Good_Privacy). It turns out factoring prime numbers while simple, is time consuming. And dividing is easy. And somehow some nerd somewhere discovered with decent certainty they can be generated. It's insanity, really. But something about the shoulders of giants...
Opsec
Even if for now it's just symmetrically encrypting files. Don't leave keys around in plaintext, ever.


```
lemon:/tmp $ echo "a stellar wallet private key is only 56 bytes" > stellarprivatekey.txt
lemon:/tmp $ wc -c privatekey.txt 
46 privatekey.txt
lemon:/tmp $ head -c 10 /dev/urandom >> stellarprivatekey.txt 
lemon:/tmp $ !w
wc -c privatekey.txt 
56 privatekey.txt
lemon:/tmp $ gpg -c stellarprivatekey.txt 
gpg: gpg-agent is not available in this session
lemon:/tmp $ ls st*
stellarprivatekey.txt  stellarprivatekey.txt.gpg
lemon:/tmp $ srm stellarprivatekey.txt                          # Delete the plaintext original.
lemon:/tmp $ cp stellarprivatekey.txt.gpg ~/Dropbox/coldstorage # Save the encrypted version to the cloud.
lemon:/tmp $ 
```

You now have a ~100 byte file that is secure that you can store whever you see fit, with the pice of mind that all needs to do to decrypt is know the passphrase and, ```gpg filename.gpg```

TODO: link or touch on proper pgp public key usage.

### Don't use a shitty browser.

Every year, at the pwn2own conference teams try to hack modern browsers. Everyone gets owned, always. In what can only be described as art.

And they do this for free, first prize is usually <100k, which is probably the [going rate for a shitty wordpress](https://www.forbes.com/sites/andygreenberg/2012/03/23/shopping-for-zero-days-an-price-list-for-hackers-secret-software-exploits/#369663282660) exploit on the black market.

As a rule of thumb, **just use Chrome**. If you prefer Firefox, that's OK too.


### Lock down your phone.

At a minimum:

  - Call your cellular provider and install a PIN CODE or pass phrase that isn't just your SSN. Assume your [SSN is public record](https://www.youtube.com/watch?v=Erp8IAUouus).
  - Try to avoid giving your real number to anyone. Google Voice used to be a thing.
  - Do not skimp or pirate your phone. Buy it from a real reseller.
  - *probably just use an iphone*


### 2fa on all the things.

    - TODO: touch on hardware 2fa's, iterate that SMS 2fa is ill-advised

### Use a password manager, but not for your email.


### Don't make yourself a target

Don't talk about crypto in real life. Probably don't hang out in Rio slums rocking a "HODL" t-shirt. Like in life in general, don't attract unnecesary attention. Walk with confidence and keep your head up.


### Different environments for different tasks

  TODO: what OS should I run?

     probably os x. linux if it's your thing. avoid windows (security tradeoffs for what is amazing backwards compatability).

  TODO: touch vms, containers, whonix/tor+tails

     Use a separate computer for gaming and general purpose shit than you do to handle sensitive tasks (crypto/secure chat).

  TODO:

     Never install any pirated software. Don't install software in general, just use a browser.


### Trust noone and nothing.

It's always an inside job. The wife did it.

What software is your exchange using? How do they send emails? They surely aren't doing that shit in house, because it's a logistical nightmare. Sendgrid? How are those password reset emails being sent. How many hops are on the wire? At any point is a key phrase transmitted in plain text enough?

### Homework: Play the "RED TEAM"

Hack yourself. Honestly. Fuck with yourself. Use your girlfriends computer knowing your all your passwords and see what you can do.

Turn your computer off, boot it off a thumb stick and pretend it's a forensic'd image. How far can you get and why?

If you, knowing yourself with complete and perfect information, were to try to make your life hell. How would you do it?


### OPSEC and Identity contamination.

https://grugq.github.io/

### Most AV's are liabilities.

https://twitter.com/taviso/status/922517900702793728
https://googleprojectzero.blogspot.com/2016/06/how-to-compromise-enterprise-endpoint.html


