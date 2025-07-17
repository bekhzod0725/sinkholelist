# sinkholelist
My Domain Sinkhole List

 * **adtracklist**
   This is a DNSBL list which can be added to any DNS blocker such as PiHole. To add it to pfBlockerNG, it has to be added under DNSBL Groups.
   
 * aiplatforms_custom_unbound_view
   This is a Unbound format to block AI-chat platforms. Created as a separate view (in this case for Kids devices). The contents of the file can be simply added to the "Custom Options" of Unbound, or can be downloaded into `/var/unbound/<filename>.conf` and called via `server:include: /var/unbound/<filename.conf>` from "Custom options"
