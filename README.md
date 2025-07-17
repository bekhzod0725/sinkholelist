# sinkholelist
My Domain Sinkhole List

 * **adtracklist**
   
   This is a DNSBL list which can be added to any DNS blocker such as PiHole. To add it to pfBlockerNG, it has to be added under DNSBL Groups.
   
 * aiplatforms_custom_unbound_view
   
   This is a Unbound format to block AI-chat platforms. Created as a separate view (in this case for Kids devices). The contents of the file can be simply added to the "Custom Options" of Unbound, or can be downloaded into `/var/unbound/<filename>.conf` and called via `server:include: /var/unbound/<filename.conf>` from "Custom options"

   The following is the format of the file, where some IPs will most likely need to be changed to fit your needs.
   ```
   server:
      access-control-view: 10.0.2.101/32 kids
      access-control-view: 10.0.2.102/32 kids

   view:
      name: "kids"
      view-first: yes
      local-data: "ahrefs.com. 900 IN A 10.1.3.85"
      local-data: "aichatting.net. 900 IN A 10.1.3.85"
   ```

   `access-control-view: 10.0.2.101/32 kids`
     * 10.0.2.101/32 - is the IP address of each device that need be added to the view
     * kids - name of the view, should match the `name` field of the `view` section

   `local-data: "ahrefs.com. 900 IN A 10.1.3.85"`
     * 10.1.3.85 - is the target IP where the domain name should be redirected to. Replace it with your webserver's IP where you wish to display a custom error message.
