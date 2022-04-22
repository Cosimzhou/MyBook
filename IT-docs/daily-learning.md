
# Dependence Inject


# libunwind
The libunwind API makes it trivial to implement the stack-manipulation aspects of exception handling. The libunwind API makes it trivial for debuggers to generate the call-chain (backtrace) of the threads in a running program. It is often useful for a running thread to determine its call-chain.

# Accumulo
Apache Accumulo is a highly scalable sorted, distributed key-value store based on Google's Bigtable. It is a system built on top of Apache Hadoop, Apache ZooKeeper, and Apache Thrift. Written in Java, Accumulo has cell-level access labels and server-side programming mechanisms.

# Covariance
Covariance represent the relationship between two variables. If covariance is 0, it means they are uncorrelated.

# Gosper's Hack
An algorithm to list all the k elements subset in a n elements set. You can use the binary sequence to represent the elements selection state. Travel from the 0..0111..1 to the 111..10..0. The key operation is how do you transfer the current binary to next one. You can follow this rule: turn the last 01 to 10 and move all of the 1 is on right side of this 01 to the least bits.

void GospersHack(int k, int n) {
    int curmask = (1 << k) - 1;
    int limit = (1 << n);
    while (curmask < limit) {
        // do something
        int last_bit = cur_mask & -cur_mask;   // the last bit which is 1
        int last_01_10 = cur_mask + last_bit;
        int least_1_bits = (last_01_10 ^ cur_mask) >> (__builtin_ctz(last_bit) + 2);
        cur_mask = least_1_bits | last_01_10;
    }
}


# Pollard Rho
It's a factor resolving algorithm.
Like Floyd cycle detection algorithm (Tortoise and Hare Algorithm), a random number loop could help to tell whether the number is a factor of given big number.


# Miller-Rabin prime test
As Fermat's little theorem says, prime p and a!=np, than a^(p-1)=1(mod p). The reverse method is Fermat method. Fermat method take a array of 'a' to test.
The sequence a^((2^r)d) mod p, r=1, 2, 3... should be all one or the first element is minus one. If this condition satisfies, it might be a prime. The 'a' array 2, 325, 9375, 28178, 450775, 9780504, 1795265022  satisfies all the number less than 2^64. It is the Miller-Rabin prime test.
Monte Carlo method.

# Ransac
RANdom SAmple Consensus. Random sampling some data as a data set. Fit this sub data set with least square method and so on. Take this fitting model to check whether fit all of the sample, compute a total residual. Compute how many loop should this process run by possibility. If there is a good enough result or the iteration overcomes the loop limit, the loop exits.


# Camera Model
Taylor formula


# Least Square Method


# Maximum Likelihood Estimation
Compute the product L of all of the samples possibility. Calculate the partial derivative logarithm of L for arguments.


# Nginx
Multi-processes and single thread reverse proxy. There is a master process of listening to the serving port and sending the request to a worker process to deal. It supports the HTTP/HTTPS protocol.
Nginx provides 5 shuffle methods to refer to the RS server. IP-hash, URL-hash, and so on.


# LVS
LVS has two working modes. They are NAT and DR.
NAT changes the destination IP address and port into the RS (Real Server) and forwards the IP packet to the RS. When RS dealt with the request, the response packet will return to LVS, and LVS modifies the destination IP address and port back to its own, before responding the packet to clients.
DR changes the data-link layer address rather than the IP layer, and all RS implements the same loopback address as LVS's. When LVS receives a datagram in the data-link layer,  the datagram will be forwarded to RS and the RS accepts it because the MAC address refers to itself, and the IP address looped back. After the RS dealing with it, the response will return to the real client rather than LVS, because there is no broker in RS's sight.

Advantages: DR is much more efficient than NAT, because of the lower implementation. And the responding data will not pass the LVS server. Usage is simple. A shorter responding path and a lower implementation make DR very awesome.
Disadvantages: DR LVS could not be deployed together in the same machine or in the different subnetworks. The configuration method is not so rich.


# Singleton:
Lazy mode & Hungary mode
Hungary mode is very simple and no need to worry about the synchronizing matter.
The lazy mode is efficient, but some matters should be dealt with. For example, the thread-safety needs a lock, but the lock will lower the speed of runtime. To solute this deadlock, we involve the double-check & lock method.

In some languages, the reflect and un-marshal would break the singleton mechanic down. There are some tricks to avoid those things happen.


