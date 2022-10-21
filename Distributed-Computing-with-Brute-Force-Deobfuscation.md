SHAREM can perform brute-force deobfuscation across several worker nodes by enabling the distributed mode, allowing the user to leverage many machines to increase efficiency and decrease decoding times. The worker nodes do not need the SHAREM script itself, only the dispynode.py script supplied with the dispy package for Python. Each worker node’s IPv4 address should be supplied in the nodes file, one address per line.

![image23](https://user-images.githubusercontent.com/114108866/192071996-6b40cfce-3769-4c5a-9ecc-8a21a724252f.png)

To use distributed computing, first run the dispynode.py script on each worker node. This script is a listener that will wait for a master node to give it a job. On the main machine, enable distributed mode and run the decryption feature by typing _g_ in the brute-forcing menu. The master node will pass each worker node a subset of keys to try, increasing efficiency of the brute-forcing process. Additionally, each node will automatically utilize CPU parallelization, taking advantage of all the CPU cores available on each machine.

Distributed computing can vastly reduce time cost for three operations, e.g. add, sub, xor. With one machine at parallel, it might be 18 hours, as there are a vast number of permutations, but with distributed and two machines, this is down to 2.5 hours. (Additional time saved may be possible with other machines or nodes - untested.)