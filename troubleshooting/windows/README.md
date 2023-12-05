Look at the ["Troubleshooting for Windows" Wiki Page](https://github.com/Campus-Castolo/m129/wiki/troubleshooting-on-windows) for more context

### Built-in Troubleshooting Tool

1. **Description:**
   - The built-in troubleshooting tool in Windows is designed to diagnose and resolve network issues automatically. It runs a series of diagnostic tests to identify problems and provides recommendations for fixing them.

2. **Two/Three Most Important Options:**
   - **Access the Troubleshooting Tool:** Right-click on the internet connection button on the taskbar.
   - **Initiate Troubleshooting:** Select the option for troubleshooting or diagnosing network problems.
   - **Follow On-Screen Instructions:** The tool guides the user through diagnostic tests.

3. **Example Output:**
   ```plaintext
   Troubleshooting Report:
   - Issue: No Internet Connection
   - Actions Taken: Reset network configurations
   - Recommendation: Restart the router
   
   Internet Connection Status:
   - Before: Unstable
   - After: Stable
   ```

4. **Errors/Problems Detected:**
   - Connectivity issues such as no internet connection.
   - Problems with network configurations.
   - Recommendations for fixing identified issues.

### Ping

1. **Description:**
   - The "ping" command checks the status of TCP/IP connections in a network. It helps diagnose issues related to network cards, gateways, and name resolution.

2. **Two/Three Most Important Options:**
   - **Ping the Loopback Address:** `ping 127.0.0.1` checks TCP/IP installation.
   - **Ping Own IP Address:** `ping 192.168.0.100` checks network card functionality.
   - **Identify Name Resolution Issues:** Compares pinging IP vs. hostname.

3. **Example Output:**
   ```plaintext
   Pinging 127.0.0.1 with 32 bytes of data:
   Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
   
   Pinging 192.168.0.100 with 32 bytes of data:
   Reply from 192.168.0.100: bytes=32 time=2ms TTL=128
   ```

4. **Errors/Problems Detected:**
   - Packet loss in the LAN.
   - High response times indicating hardware issues.

### Route

1. **Description:**
   - The `route` command displays and manipulates the IP routing table on the host.

2. **Two/Three Most Important Options:**
   - **`route print`:** Displays the current IP routing table.
   - **`route add`:** Adds a new route.
   - **`route delete`:** Deletes a route.

3. **Example Output:**
   ```plaintext
   Network Destination  Netmask          Gateway       Interface  Metric
   0.0.0.0              0.0.0.0          192.168.1.1   192.168.1.2   20
   ```

4. **Errors/Problems Detected:**
   - Incorrect or missing routing entries.
   - Gateway issues affecting network communication.

### tracert

1. **Description:**
   - The `tracert` command provides a list of routers between the user's computer and a specified destination address. It helps identify the path of network traffic.

2. **Two/Three Most Important Options:**
   - **`tracert [destination]`:** Initiates the trace route to the specified destination.
   - **ICMP Filters:** Requires deactivated ICMP filters on routers for accurate results.

3. **Example Output:**
   ```plaintext
   Tracing route to example.com [192.168.1.1]
   over a maximum of 30 hops:
   
   1    <1 ms    <1 ms    <1 ms  192.168.1.1
   ```

4. **Errors/Problems Detected:**
   - Identifies routers on the path.
   - Issues with routers discarding packets due to expired TTL values.

### pathping

1. **Description:**
   - `pathping` combines the functionality of `ping` and `tracert`, providing additional information by sending test packets to each router on the way to the specified destination.

2. **Two/Three Most Important Options:**
   - **`pathping [destination]`:** Initiates the route-tracing tool.
   - **Periodic Packet Sending:** Sends test packets over a defined period.
   - **Packet Loss Identification:** Determines where in the transmission path packets have been lost.

3. **Example Output:**
   ```plaintext
   Tracing route to example.com [192.168.1.1]
   over a maximum of 30 hops:
   
   0  Your_Computer [192.168.0.2]
   1  Router_1 [192.168.0.1]  (Approximate round trip times in milliseconds)
             5ms
   2  Router_2 [192.168.1.1]
             10ms
   ```

4. **Errors/Problems Detected:**
   - Identifies packet loss and the specific router where it occurs.
   - Helps identify overloaded routers.

### arp

1. **Description:**
   - The `arp` command detects errors in name resolution between MAC and IP addresses. It displays entries in the ARP cache and allows modifications.

2. **Two/Three Most Important Options:**
   - **`arp -a`:** Displays ARP cache entries.
   - **`arp -d [ip_address]`:** Deletes a specific ARP cache entry.
   - **`arp -s [ip_address] [mac_address]`:** Adds a static ARP entry.

3. **Example Output:**
   ```plaintext
   Interface: 192.168.0.2 --- 0x2
   Internet Address      Physical Address      Type
   192.168.1.1            00-1a-2b-3c-4d-5e     dynamic
   ```

4. **Errors/Problems Detected:**
   - Inconsistencies between MAC and IP addresses.
   - Issues with ARP cache entries.

### ipconfig

1. **Description:**
   - The `ipconfig` tool provides network configuration parameters and offers options for resolving network issues.

2. **Two/Three Most Important Options:**
   - **`ipconfig /flushdns`:** Clears the DNS name cache.
   - **`ipconfig /registerdns`:** Renews DHCP leases and re-registers DNS names.
   - **`ipconfig /displaydns`:** Shows entries in the DNS resolver cache.

3. **Example Output:**
   ```plaintext
   Windows IP Configuration

   Ethernet adapter Local Area Connection:
   
      Connection-specific DNS Suffix  . : example.com
      IPv4 Address. . . . . . . . . . . : 192.168.1.2
      Subnet Mask . . . . . . . . . . . : 255.255.255.0
   ```

4. **Errors/Problems Detected:**
   - DNS resolution issues.
   - Problems with DHCP leases.
   - Information about the network configuration.

### netstat

1. **Description:**
   - The `netstat` tool provides protocol statistics and lists current TCP/IP connections.

2. **Two/Three Most Important Options:**
   - **`netstat -a`:** Shows all connections and their associated ports.
   - **`netstat -r`:** Displays the content of the routing table.
   - **`netstat -s`:** Provides protocol statistics.

3. **Example Output:**
   ```plaintext
   Active Connections

   Proto  Local Address          Foreign Address        State
   TCP    192.168.1.2:56789      203.0.113.1:80         ESTABLISHED
   ```

4. **Errors/Problems Detected:**
   - Identifies active connections and their states.
   - Provides insights into routing table content.
   - Protocol-specific statistics.

### nslookup

1. **Description:**
   - `nslookup` is a tool for troubleshooting DNS problems, providing information about name resolution for hosts.

2. **Two/Three Most Important Options:**
   - **`nslookup [hostname]`:** Retrieves the IP address associated with a particular host.
   - **`set debug` or `set d2`:** Activates debug mode for a more detailed analysis.

3. **Example Output:**
   ```plaintext
   Server:  UnKnown
   Address:  192.168.1.1

   Non-authoritative answer:
   Name:    example.com
   Addresses:  203.0.113.1
   ```

4. **Errors/Problems Detected:**
   - Issues with DNS name resolution.
   - Provides detailed information about DNS configuration.
   - Debug mode for more in-depth analysis.

### nbtstat

1. **Description:**
   - The `nbtstat` tool troubleshoots NetBIOS name resolution issues.

2. **Two/Three Most Important Options:**
   - **`nbtstat -c`:** Shows the mapping of NetBIOS names to IP addresses in the name cache.
   - **`nbtstat -R`:** Empties the name cache and reloads entries from the LMHOSTS file.

3. **Example Output:**
   ```plaintext
   Local Area Connection:
   Node IpAddress: [192.168.1.2] Scope Id: []

       NetBIOS Remote Machine Name Table

       Name               Type         Status
   ---------------------------------------------
   EXAMPLE-HOST       <00>  UNIQUE      Registered
   ```

4. **Errors/Problems Detected:**
   - Troubleshoots NetBIOS name resolution issues.
   - Shows the mapping of NetBIOS names to IP addresses.
   - Provides options to clear and reload the name cache.

