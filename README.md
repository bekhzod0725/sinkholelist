---

# sinkholelist
This is a Domain Sinkhole List created by me. A collection of domain sinkhole lists for various use cases.

### **adtracklist**

A DNSBL (Domain Name System-based Blackhole List) for blocking ad and tracking domains. This list can be used with any DNS blocker (e.g., PiHole).

To add it to **pfBlockerNG**, you need to include it under DNSBL Groups.

---

### **aiplatforms\_custom\_unbound\_view**

A custom Unbound configuration to block AI chat platforms, intended for kid devices. This is based on [@Caesarovich](https://github.com/Caesarovich)'s ["DNS blocklist for AI Tools"](https://github.com/Caesarovich/dns-blocklist-ai), except `duckduckgo.com` was removed from the list.

You can add the contents to Unbound's "Custom Options" or download it directly to `/var/unbound/<filename>.conf` and reference it using:

```plaintext
server:include: /var/unbound/<filename>.conf
```

#### File Format

Below is an example configuration:

```plaintext
server:
   access-control-view: 10.0.2.101/32 kids
   access-control-view: 10.0.2.102/32 kids

view:
   name: "kids"
   view-first: yes
   local-data: "ahrefs.com. 900 IN A 10.1.3.85"
   local-data: "aichatting.net. 900 IN A 10.1.3.85"
```

#### Explanation of Configuration

* **access-control-view**:

  * `10.0.2.101/32` and `10.0.2.102/32` are the IP addresses of the devices that should use this view (e.g., kids' devices).
  * `kids` is the name of the view and should match the `name` field in the `view` section.

* **local-data**:

  * `10.1.3.85` is the IP address where the domain should be redirected. Replace it with the IP of your webserver or device that will serve a custom error message.
  * Example:
    `local-data: "ahrefs.com. 900 IN A 10.1.3.85"`

---
