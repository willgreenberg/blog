---
title: "Flicking the light switch - illuminating the big scary Internet"
date: 2017-08-23T15:06:06-04:00
draft: false
---

Imagine standing in a pitch black room. You’ve been there a ton. In fact, you know how to get to all kinds of things around you. You walk over here to order a toaster on Amazon. You walk over there to RSVP to your friend’s birthday bar crawl. You turn around, take a few steps forward, and reach to your left to send a tweet.

But you can’t see any of it. You’ve never seen any of it. You have no clue what lies between you and Twitter, or Amazon, or Facebook. You might be used to it — I think it’s fair to say most of us are *too* used to it.

Christian Ternus gave a wonderful talk on the basics of networking and the Open Systems interconnection model, OSI, that essentially outlines the functionality of connections over the internet from the ground up. You could learn a whole lot from the Wikipedia pages on this stuff, but Christian’s conversational approach made it actually digestible. I’m going to try and do something similar here.
...
I know! It’s intimidating! But consider — this stuff is omnipresent. It’s ridiculously important. Every day it seems both more difficult to grasp and more difficult to get away from. Taking the magic out of it makes it less scary - it’s easy to fear what you don’t understand. Imagine flicking the light on in a pitch black room.

# OSI Model Layers:

## **Hardware**
### 1. **Physical** - *Bits* - WiFi
  - Hardware layer
  - Less critical for software developers (not interfaced programmatically) but good to know about since this stuff could indeed affect performance

## **Kernel**
### 2. **Data Link** - *Frames* - Ethernet
  - 1 Frame ~= 1500 bytes
  - Provides node-to-node data transfer through a link directly between two nodes
  - MAC (Media Access Control) - controls how devices on a network gain access to a medium and permission to transmit data

### 3. **Network** - *Packets* - IP (Internet Protocol)
  - IPv4 - 4 bytes, 0.0.0.0 to 255.255.255.255
    - Originally considered *enough* addresses for everyone ... back in the 70s before the internet was essentially omnipresent.
  - IPv6 - 6 bytes, 0.0.0.0.0.0 to 255.255.255.255.255.255
    - Introduced in the 90s, this time with the intention of truly having enough addresses for *everyone*
    - Problem is ... plenty of legacy addresses were left stuck with hard coded IPv4 addresses. Many places still today don't have IPv6 addresses.

    What's the problem here? IPv6 addresses are not supported by lots of devices (i.e. early Android, Windows XP). [Come back to this re tunnel, translation]

### 4. **Transport** - *Segments* - TCP (Transmission Control Protocol), UDP
  - Need a way to break up a bunch of data, since a packet can only hold about 1500 bytes.
  - Jigsaw Puzzle - Imagine a client (user's computer) sends information as a collection of puzzle pieces (packets); each piece is numbered. TCP provides ways for the server to let the client know that "hey, I've gotten a few of those pieces, keep 'em coming." or "you didn't send me piece number 6273!".
  - For a TCP connection to be established, a server first has to be listening at a port for a connection to open up (known as a "passive open"). A client can initiate an active open to establish the connection - establishing the connection entails a "three way handshake":
    1. SYN: the client sends a SYN (synchronize) packet to the server, saying "I want to connect with you." In this message the client sets a sequence number for the segment to some random number, call it A (less than about 30,000).
    2. SYN/ACK: the server responds with a SYN/ACK (synchronize/acknowledge) packet sent to the client. It contains an acknowledgement number set to A + 1.
    3. ACK: the client responds again with an ACK packet

## **User**

### 5. **Session** - *Sockets*


### 6. **Presentation** - *SSL (Secure Sockets Layer)*
  - Maybe a server wants to guarantee a client is who they claim to be - that's authentication. Maybe a client wants to ensure that they are connecting to the right server - that's [something].
  - Public Key and Private Key
    - A certificate is a published public key.
    - Anybody with that public key can use it

### 7. **Application** - *HTTP, SMTP, SSH, etc.*

Post Office analogy

Frames - plastic buckets of mail
Packets -
