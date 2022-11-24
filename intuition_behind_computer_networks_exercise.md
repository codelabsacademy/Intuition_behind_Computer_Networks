# Intuition behind Computer Networks - Exercise Solution


## Exercise Setup
You are presented with the follwoing network:

![exercise](https://res.cloudinary.com/clacontent/image/upload/v1668478436/workshops/cn_exercise_g8fddd.png)

You will be placed at the position that is represented by the eye. The user on the computer on the left types in "codelabsacademy.com" on their browser. Your goal is to list all the packets that will pass the link you are placed at. Specifically, for each packet, write down its
* source MAC address,
* destination MAC address,
* source IP address,
* destination IP address,
* source port number,
* destination port number,
* whether it is using TCP/UDP,
* the protocol that is used.



## Solution

|  # | **src MAC**       | **dst MAC**       | **src IP** | **dst IP** | **src port nr** | **dst port nr** | **UDP/TCP** | **Protocol**   |
|:--:|-------------------|-------------------|------------|------------|-----------------|-----------------|-------------|----------------|
| 1  | aa:bb:cc:dd:ee:12 | ff:ff:ff:ff:ff:ff | /          | /          | /               | /               | /           | ARP (Request)  |
| 2  | dd:dd:dd:dd:dd    | aa:bb:cc:dd:ee:12 | /          | /          | /               | /               | /           | ARP (Reply)    |
| 3  | aa:bb:cc:dd:ee:12 | dd:dd:dd:dd:dd:dd | 1.1.1.1    | 2.2.2.10   | 4500            | 80              | UDP         | DNS (Query)    |
| 4  | dd:dd:dd:dd:dd:dd | aa:bb:cc:dd:ee:12 | 2.2.2.10   | 1.1.1.1    | 80              | 4500            | UDP         | DNS (Response) |
| 5  | aa:bb:cc:dd:ee:12 | ff:ff:ff:ff:ff:ff | /          | /          | /               | /               | /           | ARP (Request)  |
| 6  | aa:bb:cc:dd:ee:22 | aa:bb:cc:dd:ee:12 | /          | /          | /               | /               | /           | ARP (Reply)    |
| 7  | aa:bb:cc:dd:ee:12 | aa:bb:cc:dd:ee:22 | 1.1.1.1    | 3.3.3.1    | 4501            | 80              | TCP         | TCP SYN        |
| 8  | aa:bb:cc:dd:ee:22 | aa:bb:cc:dd:ee:12 | 3.3.3.1    | 1.1.1.1    | 80              | 4501            | TCP         | TCP SYN/ACK    |
| 9  | aa:bb:cc:dd:ee:12 | aa:bb:cc:dd:ee:22 | 1.1.1.1    | 3.3.3.1    | 4501            | 80              | TCP         | TCP ACK        |
| 10 | aa:bb:cc:dd:ee:12 | aa:bb:cc:dd:ee:22 | 1.1.1.1    | 3.3.3.1    | 4501            | 80              | TCP         | HTTP GET       |
| 11 | aa:bb:cc:dd:ee:22 | aa:bb:cc:dd:ee:12 | 3.3.3.1    | 1.1.1.1    | 80              | 4501            | TCP         | HTTP OK        |