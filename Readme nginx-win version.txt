
=== This is NGINX for Windows, an event driven, non-blocking high performance full
featured webserver based on nginx.

HTTP/2, multiple workers, ASLR and DEP compliant, embedded WAF, embedded Lua are just
a few features to mention. ===

** Why do I have to pay for your version?
=> You don't have to pay anything, what you find here is FREE !
However, if you want professional support or a custom version then you need a
commercial subscription.


Note: Should you need support or report anything please use email
support@ecsystems.nl (where we maintain the package builds)

CVE: any security issues such as vulnerabilities should be reported by email
support@ecsystems.nl (start the subject line with "CVE:"), a security engineer
ticket will be created and dealt with a.s.a.p.

Builds can be found here:
  http://nginx-win.ecsds.eu/
  Follow releases via RSS http://nginx-win.ecsds.eu/nginx-win-rss.xml.rss
  (Yes we support TLS but only via our own root CA at http://ca1.ecsystems.nl)

Todo:
- allow multiple instances to run on the same machine
- More non-blocking Lua, event based DLL add-on’s like pagespeed, SharePoint, asp/dotnet.
- Full 64 bit builds.
- IO event and thread separation (100% completed. testing on AWS).
  Depending on your CPU/GPU this feature will activate automatically and yes we utilize the GPU as well
- Distributed IO and CPU event processing (100% completed. testing on AWS)

Feature list (* included with nginx_basic):
=* All current nginx features (see with nginx.exe -V) (subject to Windows compatibility)
=* Consistent with original nginx code (subject to Windows compatibility)
=* FD_SETSIZE = 32768 (modded kernel), allows one worker to handle c250k+
   (with optimization registry file)
=* Multiple workers supported ! use no more than 2 workers for 1 core (cpu)
=* HTTP/2
=* Cloudflare dynamic_TLS_records
=  LuaJIT compiled in (lua-nginx-module)
=* PCRE JIT enabled
=  Naxsi WAF - Web Application Firewall
=  Array-var-nginx-module
=  HttpSubsModule
=  echo-nginx-module
=  ngx_http_lower_upper_case
=  headers-more-nginx-module
=  set-misc-nginx-module
=  ngx_http_auth_ldap
=* Additional custom 503 error handler via 513
=  lua-upstream-nginx-module (Manipulate upstream dynamically)
=* Select-boost, Wpoll
=* Fully ASLR and DEP compliant for shared memory
=  encrypted-session-nginx-module
=  Nginx-limit-traffic-rate-module
=  AJP - tomcat backend support
=  form-input-nginx-module
=  ngxLuaDB, the drizzle and dynamic loaded module solution
=  ngx_upstream_jdomain
=  cache_purge
=  nginx-http-concat
=  nginx-module-vts (Virtual host traffic status)
=* "Proxy-Authenticate" header for the 407 response
=* 'include' in upstream
=  stream-echo-nginx-module
=  stream-lua-nginx-module
Commercial subscription only modules:
=  nginx-sticky-module
=  Lua based lawful interception
=  Streaming with nginx-rtmp-module
=  nginx-vod-module (On-the-fly repackaging of MP4 files to DASH, HDS, HLS, MSS)
These native builds run on Windows XP SP3 and higher, both 32 and 64 bit.


*** Default installation instructions;
* New: unzip this version with folder structure
* Old: overwrite with this version
* Check nginx.conf, nginx-org.conf and nginx-win.conf
* Windows optimization registry file: check your current values BEFORE setting the new ones

*** Integrated installation instructions;
We have thought about building an installer but it seems far easier to lean on existing
combined packages which have nginx for Windows included, mind you these packages use
the official (limited) windows build by nginx but it is extremely easy to replace nginx.exe
with our version. For the most easiest replacement overwrite nginx.exe with nginx_basic.exe
from our package. If you want Lua and all the other advanced functions overwrite nginx.exe
with nginx.exe, place lua51.dll in the same folder as nginx.exe from our package and don't
forget to install vcredist_x86.exe or vcredist_x64.exe.
Example integrated packages are:
http://wtriple.com/wtnmp/
http://wpn-xm.org/
http://winginx.com/en/
A word of warning: keep in mind that integrated packages need to be kept up to date, that
means php, mysql, etc. all need to be upgraded whenever possible.
*** Anyway, we've made something :) see Install_nginx_php_services.zip on site.


Upgrade Assessment Matrix
----------------------------
I am using                    Security Stability Performance Existing_Features New_Features Scalability
----------------------------  -------- --------- ----------- ----------------- ------------ -----------
nginx 1.21.7.1 WhiteHorse     None     None      Medium      Medium            None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.21.7.2 WhiteHorse     Low      None      None        None              None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.1.1 SnapDragonfly  Low      None      None        None              Medium       None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.3.1 SnapDragonfly  Low      None      None        None              Medium       None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.3.2 SnapDragonfly  Low      None      None        None              Medium       None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.3.3 SnapDragonfly  Low      None      None        None              None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.3.4 SnapDragonfly  Low      None      None        None              None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.3.5 SnapDragonfly  Low      Low       None        Low               None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.23.3.6 SnapDragonfly  Low      Low       Low         None              None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.25.4.1 SnapDragonfly  None     None      None        Low               Low          None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.25.4.2 SnapDragonfly  Low      None      None        None              None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------
nginx 1.27.1.1 SnowDrop       None     None      None        None              None         None
----------------------------  -------- --------- ----------- ----------------- ------------ ------------


12:36 29-Nov-2024 nginx 1.27.1.1 SnowDrop

This time of the year we don't like to be accused of misbehaving and pulling SnowDrop away from the milk
before her, ain't we male or female, do we stir our tail when we like what we see which is speed!

Based on best code from nginx and freenginx 1.27 (27-Nov-2024) with;
* Fixes in: openssl, mp4, core, proxy, upstream, mail, realip
* Dropped nginx web forum support as it moves to Git
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:43 11-Sep-2024 nginx 1.25.4.2 SnapDragonfly

Based on best code from nginx and freenginx 1.27 (30-8-2024) with;
* Fixes in: mp4, ssl_preread, openssl, pcre, resolver
+ Openssl 3.0 (LTS) 3.0.15
* 5-Jun-2024: the 4 Jun/1.25.4.1 release is only a recompile (Openssl) version (Fastlane)
* CVE-2024-32760 does not effect our version
* CVE-2024-34161 does not effect our version
* CVE-2024-35200 does not effect our version
* CVE-2024-31079 does not effect our version
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


08:56 28-May-2024 nginx 1.25.4.1 SnapDragonfly

Based on nginx and freenginx 1.27 (21-5-2024) with;
* Fixes in: headers, ip-mapping, http, mail, proxy, redirection, stream-pass, openssl, upstream, file-indexing
* Experimental MPTCP support (Dourov Maxime / RFC8684 - listen ... mptcp) Kernel or (virtIO)driver support needed
* Actively tested for IPv6 production use
* CVE-2024-31497 does not effect our version
* CVE-2024-3094 does not effect our version
* There is clearly a battle going on between nginx and freenginx, until (if ever) this is played out 
  we'll do our own thing and sit on the fence on who's (new) code/fixes is the best choice for Windows
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:59 14-Feb-2024 nginx 1.23.3.6 SnapDragonfly

Based on nginx 1.25.4 (31-1-2024) with;
+ Quickfix for Segfault / cached X-Accel-Redirect (9-Feb-2024)
+ Openssl 3.0 (LTS) 3.0.13
+ zlib-1.3.1
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


13:09 2-11-2023 nginx 1.23.3.5 SnapDragonfly

Based on nginx 1.25.3 (24-10-2023) with;
+ Openssl 3.0 (LTS) 3.0.12
* Naxsi CVE-2023-45132 does not effect our version
+ HTTP/2: per-iteration stream handling limit. Not really needed but adopted (CVE-2023-44487)
* nginx 1.23.3... forever? we stay on this branch for now, which is 1.25/7 minus QUIC
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


17:52 11-9-2023 nginx 1.23.3.4 SnapDragonfly

Based on nginx 1.25.3 (3-9-2023) with;
+ Fix for Openssl CVE-2023-4807
+ Openssl 3.0 (LTS) 3.0.10
+ zlib-1.3
* Openssl 3.0 EOL??? Some other products are mis-informing you:
  https://www.openssl.org/policies/releasestrat.html
  "Version 3.0 will be supported until 2026-09-07 (LTS)."
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


09:49 4-6-2023 nginx 1.23.3.3 SnapDragonfly

Based on nginx 1.25.0 (20-4-2023) with;
* We don't consider QUIC to be stable or secure enough yet
* prove14 released
+ Openssl 3.0 (LTS) 3.0.9
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


09:11 17-4-2023 nginx 1.23.3.2 SnapDragonfly

Based on nginx 1.23.4 (3-4-2023) with;
+ Openssl 3.0 (LTS) 3.0.8
* The next 3.0.* is around the corner, watch for a speedy update (1.23.3.3) when this happens
* Extended Beta period to make sure a (very small ossl 3.0) memory leak has been fixed
* New amended documentation (on going work 1.9 -> 2.0)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


14:09 9-2-2023 nginx 1.23.3.1 SnapDragonfly

Based on nginx 1.23.3 (16-12-2022) with;
+ Openssl-1.1.1t
* (Twitter is being phased out) Follow releases via RSS http://nginx-win.ecsds.eu/nginx-win-rss.xml.rss
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no (Openssl)
* Additional specifications: see 'Feature list'


11:32 24-10-2022 nginx 1.23.1.1 SnapDragonfly

'Look on the branch above your head,' said the Gnat, 'and there you'll find a SnapDragonfly.
Its body is made of plum-pudding, its wings of holly-leaves, and its head is a raisin burning in brandy.'
We all ain't that messed up, but when we are stirred we will perform!

Based on nginx 1.23.2 (19-10-2022) with;
+ zlib-1.2.13
* This version does not include/support Linked Lists
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


13:19 5-7-2022 nginx 1.21.7.2 WhiteHorse

Based on nginx 1.21.7(1.22) (1-5-2022) with;
+ Openssl-1.1.1q
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no (Openssl)
* Additional specifications: see 'Feature list'


14:20 26-5-2022 nginx 1.21.7.1 WhiteHorse

Based on nginx 1.21.7(1.22) (1-5-2022) with;
+ Openssl-1.1.1o
+ zlib-1.2.12
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:02 15-3-2022 nginx 1.21.5.2 WhiteHorse

Based on nginx 1.21.7 (5-2-2022) with;
+ Openssl-1.1.1n
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no (Openssl)
* Additional specifications: see 'Feature list'


10:05 12-2-2022 nginx 1.21.5.1 WhiteHorse

Based on nginx 1.21.7 (5-2-2022) with;
+ Openssl-1.1.1m
* At this time we do not see enough benefits for PCRE2
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:50 7-11-2021 nginx 1.21.3.1 WhiteHorse

Based on nginx 1.21.4 (3-11-2021) with;
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


14:25 28-8-2021 nginx 1.21.1.1 WhiteHorse

Based on nginx 1.21.2 (23-8-2021) with;
+ Openssl-1.1.1l
+ pcre-8.45-r1767 (upgraded 8-7-2021)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Due to a design change two prove tests need to be changed;
* Old:Naxsi_00901h3;curl -G -0 -i "http://127.0.0.1:880/?a=AND+1=1%%00 Union select 1";HTTP/1.1 412 Precondition Failed;T1
* New:Naxsi_00901h3;curl -G -0 -i "http://127.0.0.1:880/?a=AND+1=1%%00%%20Union%%20select%%201";HTTP/1.1 412 Precondition Failed;T1
* Old:Naxsi_022lib2;curl -G -0 -i "http://127.0.0.1:880/?x=1' OR '1'='1";HTTP/1.1 412 Precondition Failed;T1
* New:Naxsi_022lib2;curl -G -0 -i "http://127.0.0.1:880/?x=1'%%20OR%%20'1'='1";HTTP/1.1 412 Precondition Failed;T1
* Additional specifications: see 'Feature list'


19:14 30-5-2021 nginx 1.21.0.1 WhiteHorse

Based on nginx 1.21.0 (26-5-2021) with;
* CVE-2021-23017 has no impact on Windows
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:01 30-3-2021 nginx 1.19.9.1 WhiteHorse

Based on nginx 1.19.9 (29-3-2021) with;
+ Openssl-1.1.1k
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no, Openssl patches
* Additional specifications: see 'Feature list'


10:23 23-2-2021 nginx 1.19.7.1 WhiteHorse

The WhiteHorse with his rider The White Knight, is ready to save Alice of the Red Knight.

Based on nginx 1.19.7 (17-2-2021) with;
+ Openssl-1.1.1j
* Fix for Nginx-limit-traffic-rate-module
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


16:46 8-12-2020 nginx 1.19.5.1 Unicorn, re-released due to Openssl patches

Based on nginx 1.19.5 (24-11-2020) with;
+ Openssl-1.1.1i
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no, Openssl patches
* Additional specifications: see 'Feature list'


20:54 28-11-2020 nginx 1.19.5.1 Unicorn

Based on nginx 1.19.5 (24-11-2020) with;
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Unicorn series, watch out for the new release name


17:31 30-9-2020 nginx 1.19.3.1 Unicorn

Based on nginx 1.19.3 (29-9-2020) with;
* Known broken issues: ajp cache (ajp -without cache- works ok)
  workaround https://github.com/yaoweibin/nginx_ajp_module/issues/37#issuecomment-158076648
* Scheduled release: yes
* Additional specifications: see 'Feature list'


20:27 9-7-2020 nginx 1.19.1.1 Unicorn

Based on nginx 1.19.1 (9-7-2020) with;
+ LuaJIT-2.2.1 (fixes): lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


15:55 21-4-2020 nginx 1.17.10.1 Unicorn

Based on nginx 1.17.10 (21-4-2020) with;
+ Openssl-1.1.1g
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no (openssl CVE-2020-1967)
* Additional specifications: see 'Feature list'


13:16 3-4-2020 nginx 1.17.9.1 Unicorn

Based on nginx 1.17.10 (20-3-2020) with;
+ Openssl-1.1.1f
+ ngx_http_concat_module (upgraded 31-3-2020)
+ nginx_ajp_module-master (upgraded 31-3-2020)
+ nginx-auth-ldap-master (upgraded 31-3-2020)
+ pcre-8.44-r1764 (upgraded 29-2-2020)
+ Naxsi WAF (upgraded 29-2-2020)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:21 26-1-2020 nginx 1.17.8.1 Unicorn

Based on nginx 1.17.8 (25-1-2020) with;
+ LuaJIT-2.2.1 (fixes): lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
+ echo-nginx-module (small fix)
+ pcre-8.44-r1758 (upgraded 18-1-2020)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


12:55 26-11-2019 nginx 1.17.6.1 Unicorn

Based on nginx 1.17.6 (20-11-2019) with;
+ pcre-8.44-r1757 (upgraded 20-11-2019)
+ LuaJIT-2.2.1 (fixes): lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


17:49 29-9-2019 nginx 1.17.4.1 Unicorn

Based on nginx 1.17.4 (26-9-2019) with;
+ LuaJIT-2.2.1 (fixes): lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
+ Openssl-1.1.1d
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:56 14-8-2019 nginx 1.17.3.1 Unicorn

"Do you know, I always thought unicorns were fabulous monsters, too?
I never saw one alive before!"
"Well, now that we have seen each other,' said the Unicorn.
'If you'll believe in me, I'll believe in you."

Based on nginx 1.17.3 (13-8-2019) with;
+ Fixes CVE-2019-9511, CVE-2019-9513, CVE-2019-9516
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no
* Additional specifications: see 'Feature list'


16:22 28-7-2019 nginx 1.17.1.1 Crow

Based on nginx 1.17.2 (23-7-2019) with;
+ LuaJIT-2.2.1 (fixes): lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
+ pcre-8.44-r1756 (upgraded 22-7-2019)
+ nginx-auth-ldap (upgraded 22-7-2019)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Crow series, watch out for the new release name


11:50 31-5-2019 nginx 1.17.0.1 Crow

Based on nginx 1.17.0 (22-5-2019) with;
+ 28-5 patch, Use round-robin if hash key is empty
+ Openssl-1.1.1c (TLS 1.3)
*   ssl_protocols TLSv1.2 TLSv1.3;
*   ssl_prefer_server_ciphers on; 
*   ssl_ciphers EECDH+AESGCM:EDH+AESGCM:!aNULL:!eNULL:!MD5:!DSS:!EXP:!ADH:!LOW:!MEDIUM;
*   ssl_ecdh_curve secp384r1;
+ pcre-8.44-r1753 (upgraded 29-5-2019)
+ LuaJIT-2.2.1 (fixes): lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:46 6-3-2019 nginx 1.15.10.1 Crow

Based on nginx 1.15.10 (4-3-2019) with;
+ refit cloudflare dynamic_tls_records, no more settings required
+ Openssl-1.0.2r
+ pcre-8.43-r1750 (upgraded 4-3-2019)
+ LuaJIT-2.2.1: lua51.dll DO NOT FORGET TO REPLACE THIS FILE !
* Includes Wpoll, this release only stable with one cpu
  events { ...; use poll; ...; }
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


16:03 23-12-2018 nginx 1.15.8.1 Crow

Based on nginx 1.15.8 (15-12-2018) with;
* This years last version, have a good one !
+ Naxsi WAF (upgraded 15-12-2018)
+ Openssl-1.0.2q
+ pcre-8.43-r1744 (upgraded 15-12-2018)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:19 7-11-2018 nginx 1.15.6.1 Crow

Based on nginx 1.15.6 (6-11-2018) with;
+ fixes CVE-2018-16843, CVE-2018-16844, CVE-2018-16845
+ pcre-8.43-r1741 (upgraded 3-11-2018)
+ Openssl fixes CVE-2018-0734, CVE-2018-0735
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no
* Additional specifications: see 'Feature list'


10:37 7-10-2018 nginx 1.15.4.1 Crow

Based on nginx 1.15.5 (2-10-2018) with;
+ refit cloudflare dynamic_tls_records
+ lua-nginx-module (upgraded 30-9-2018)
+ pcre-8.43-r1740 (upgraded 30-9-2018)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:09 19-8-2018 nginx 1.15.3.1 Crow

Based on nginx 1.15.3 (14-8-2018) with;
+ Openssl-1.0.2p (CVE-2018-0737)
* The default for keepalive_requests is set to 1000 (was 100)
* We are working to add Brotli but having compiler isssues
+ pcre-8.43-r1738 (upgraded 19-8-2018)
+ Naxsi WAF (upgraded 16-8-2018)
+ lua-nginx-module (upgraded 11-8-2018)
+ stream-lua-nginx-module (upgraded 30-6-2018)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


15:26 12-6-2018 Rereleased for (CVE-2018-0732)
11:52 10-6-2018 nginx 1.15.0.1 Crow

Based on nginx 1.15.1 (8-6-2018) with;
+ Naxsi WAF (upgraded 1-6-2018)
+ lua-nginx-module (upgraded 1-6-2018)
+ stream-lua-nginx-module (upgraded 1-6-2018)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


16:19 7-4-2018 nginx 1.13.10.1 Crow

The Crow is here, the Red King's dramatis personae bishop, black 
as a tar-barrel and of a monstrous size.
Don't mistake it for the dread bird and flee through the woods 
while you still can. The Crow, the crow is here!

Based on nginx 1.13.12 (6-4-2018) with;
+ lua-nginx-module (upgraded 28-3-2018)
+ Openssl-1.0.2o
+ pcre-8.42-r1733 (upgraded 20-3-2018)
+ set-misc-nginx-module (upgraded 19-3-2018)
+ stream-lua-nginx-module (upgraded 19-3-2018)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


15:37 24-2-2018 nginx 1.13.9.1 Violet

Based on nginx 1.13.10 (24-2-2018) with;
+ Naxsi WAF (upgraded 24-2-2018)
+ lua-nginx-module (upgraded 24-2-2018)
+ stream-lua-nginx-module (upgraded 24-2-2018)
+ echo-nginx-module (upgraded 13-2-2018)
+ encrypted-session-nginx-module (upgraded 13-2-2018)
+ pcre-8.41-r1726 (upgraded 24-2-2018)
* Happy new year!
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Violet series, watch out for the new release name


15:17 19-12-2017 nginx 1.13.8.1 Violet

Based on nginx 1.13.7 (7-12-2017) with;
+ set-misc-nginx-module (upgraded 7-12-2017)
+ lua-nginx-module (upgraded 16-12-2017)
+ Openssl-1.0.2n (CVE-2017-3737, CVE-2017-3738)
+ pcre-8.41-r1719 (upgraded 16-12-2017)
* This years last version, have a good one !
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


21:33 16-11-2017 nginx 1.13.7.1 Violet

Based on nginx 1.13.7 (9-11-2017) with;
+ lua-nginx-module (upgraded 8-11-2017)
+ Naxsi WAF (upgraded 9-11-2017)
+ Openssl-1.0.2m (CVE-2017-3736, CVE-2017-3735)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


20:04 23-10-2017 nginx 1.13.6.1 Violet

Based on nginx 1.13.7 (23-10-2017) with;
+ headers-more-nginx-module (upgraded 8-10-2017)
+ lua-nginx-module (upgraded 8-10-2017)
+ stream-lua-nginx-module (upgraded 8-10-2017)
+ Openssl minor bug fixes
+ pcre-8.41-r1713 (upgraded 23-10-2017)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


20:29 31-8-2017 nginx 1.13.5.1 Violet

Based on nginx 1.13.5 (27-8-2017) with;
+ lua-nginx-module (upgraded 27-8-2017)
+ stream-lua-nginx-module (upgraded 27-8-2017)
+ ngx_devel_kit (upgraded 27-8-2017)
+ pcre-8.41-r1710 (upgraded 27-8-2017)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


14:37 16-7-2017 nginx 1.13.2.1 Violet

Based on nginx 1.13.4 (14-7-2017) with;
+ lua-nginx-module (upgraded 14-7-2017)
+ pcre-8.41-r1707 (upgraded 14-7-2017)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


14:53 4-6-2017 nginx 1.13.1.1 Violet

Based on nginx 1.13.2 (3-6-2017) with;
+ lua-nginx-module (upgraded 3-6-2017)
+ pcre-8.40-r1701 (upgraded 3-6-2017)
+ LuaJIT-2.0.5 (upgraded 27-5-2017)
+ lua51.dll (upgraded 27-5-2017) DO NOT FORGET TO REPLACE THIS FILE !
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:03 26-4-2017 nginx 1.13.0.1 Violet

The violet is rude but stands her ground making everyone else look stupid around
the nginx Violet release is here !

Based on nginx 1.13.0 (25-4-2017) with;
+ echo-nginx-module (upgraded 25-4-2017)
+ Naxsi WAF (upgraded 14-4-2017)
+ lua-nginx-module (upgraded 14-4-2017)
+ Openssl <-1.0.2l-import (bug fixes)
+ pcre-8.40-r1697 (upgraded 25-4-2017)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


7:27 28-3-2017 nginx 1.11.11.1 Lion

Based on nginx 1.11.12 (27-3-2017) with;
+ Added fixes for Openssl and pcre undisclosed CVE's
+ Openssl <-1.0.2l-import (bug fixes)
+ pcre-8.40-r1691 (upgraded 27-3-2017)
+ lua-nginx-module (upgraded 18-3-2017)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Lion series, watch out for the new release name


19:37 22-2-2017 nginx 1.11.10.1 Lion

Based on nginx 1.11.11 (20-2-2017) with;
+ nginx-auth-ldap (upgraded 20-2-2017)
+ lua-nginx-module (upgraded 20-2-2017)
+ pcre-8.40-r1683 (upgraded 20-2-2017)
+ Naxsi WAF (upgraded 20-2-2017)
+ SNI fixes
+ Openssl <-1.0.2l-import (bug fixes)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:46 26-1-2017 nginx 1.11.9.1 Lion

Based on nginx 1.11.9 (24-1-2017) with;
+ Openssl-1.0.2k (CVE-2017-3731, CVE-2017-3732, CVE-2016-7055)
+ pcre-8.40-r1677 (upgraded 23-1-2017)
+ stream-lua-nginx-module (upgraded 10-1-2017)
+ lua-nginx-module (upgraded 23-1-2017)
+ zlib 1.2.11 (upgraded 16-1-2017)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


0:52 24-12-2016 nginx 1.11.8.1 Lion

Based on nginx 1.11.8 (21-12-2016) with;
+ stream-lua-nginx-module (upgraded 18-12-2016)
+ lua-nginx-module (upgraded 18-12-2016)
+ pcre-8.40-r1673 (upgraded 18-12-2016)
+ nginx-auth-ldap (upgraded 6-12-2016)
* nb: StrictTimeWaitSeqCheck(1) might be causing sockets to hang
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:30 21-11-2016 nginx 1.11.7.1 Lion

Based on nginx 1.11.7 (21-11-2016) with;
+ encrypted-session-nginx-module (upgraded 6-11-2016)
+ headers-more-nginx-module (upgraded 6-11-2016)
+ stream-lua-nginx-module (upgraded 6-11-2016)
+ lua-nginx-module (upgraded 19-11-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:42 19-10-2016 nginx 1.11.6.1 Lion

Based on nginx 1.11.6 (18-10-2016) with;
+ Openssl/ngxevent zero len fix
* Promoted: https://github.com/p0pr0ck5/lua-resty-waf
+ ngx_upstream_jdomain (upgraded 15-10-2016)
* sslh, see conf/nginx-sslh-v1.0.conf
+ lua-nginx-module (upgraded 9-10-2016)
+ pcre-8.40-r1670 (upgraded 18-10-2016)
+ nginx-auth-ldap (upgraded 2-10-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:40 26-9-2016 nginx 1.11.5.1 Lion

Based on nginx 1.11.5 (22-9-2016) with;
* Push re-release due to Openssl fix
+ Openssl-1.0.2j (CVE-2016-7052)
* Scheduled release: no


13:57 22-9-2016 nginx 1.11.5.1 Lion

Based on nginx 1.11.5 (22-9-2016) with;
+ Openssl-1.0.2i (CVE-2016-6304, CVE-2016-2183, CVE-2016-6303,
  CVE-2016-6302, CVE-2016-2182, CVE-2016-2180, CVE-2016-2178,
  CVE-2016-2179, CVE-2016-2181, CVE-2016-6306)
+ Several Lua/Stream API fixes
+ config fix for: IE is displaying "NaN" and "NaN GiB"
  see 'Cache-Control' in conf\vhts\VHTS.txt
+ stream-lua-nginx-module (upgraded 5-9-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


14:00 28-8-2016 nginx 1.11.4.1 Lion

The Lion and the Unicorn are forever fighting over the White Kings crown
The lion beat the unicorn all around the town. the nginx Lion release is here !

Hey to JT!
"Got this feeling in my body, All those things I shouldn't do
 But you dance, dance, dance, I can't stop the feeling
 And ain't nobody leaving soon, so keep dancing!"

Based on nginx 1.11.4 (28-8-2016) with;
+ Naxsi WAF (upgraded 28-8-2016)
+ pcre-8.40-r1664 (upgraded 10-8-2016)
+ Added mitigation to Openssl-1.0.2h for CVE-2016-2180
+ lua-nginx-module (upgraded 21-8-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


9:07 28-7-2016 nginx 1.11.3.1 WhiteKnight

Based on nginx 1.11.3 (27-7-2016) with;
* About http://www.kb.cert.org/vuls/id/797896
  see https://access.redhat.com/security/vulnerabilities/httpoxy
  we don't see this as a server issue but as an application
  (behind nginx) issue
+ md5/sha1 API and CTX fixes across modules
+ set-misc-nginx-module (upgraded 21-7-2016)
+ stream-echo-nginx-module (upgraded 21-7-2016)
+ stream-lua-nginx-module (upgraded 21-7-2016)
+ lua-nginx-module (upgraded 21-7-2016)
+ pcre-8.40-r1663 (upgraded 21-7-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the WhiteKnight series, watch out for the new release name


11:31 3-7-2016 nginx 1.11.2.2 WhiteKnight

Based on nginx 1.11.2 (25-6-2016) with;
+ Added mitigation to Openssl-1.0.2h for CVE-2016-2177
  and CVE-2016-2178 and 4 other undisclosed CVE's
+ pcre-8.40-r1660 (upgraded 2-7-2016)
+ http2 socket leak fixes (Valentin V. Bartenev)
+ lua-nginx-module (upgraded 2-7-2016)
+ headers-more-nginx-module (upgraded 25-6-2016)
* prove12 released
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* Why using embedded Lua inside nginx (core) is so much faster:
  https://forums.ecsystems.nl/viewtopic.php?f=7&t=89
! This July 2016 only, a 50% discount on all new subscriptions !


0:09 14-6-2016 nginx 1.11.2.1 WhiteKnight

Based on nginx 1.11.2 (11-6-2016 [sha1]) with;
+ cloudflare dynamic_tls_records
  https://blog.cloudflare.com/optimizing-tls-over-tcp-to-reduce-latency/
+ stream-lua-nginx-module (upgraded 7-6-2016)
+ headers-more-nginx-module (upgraded 7-6-2016)
+ echo-nginx-module (upgraded 7-6-2016)
+ Naxsi WAF (upgraded 7-6-2016)
+ lua-nginx-module (upgraded 9-6-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


0:49 29-5-2016 nginx 1.11.1.1 WhiteKnight

Based on nginx 1.11.1 (26-5-2016) with;
+ Naxsi WAF (upgraded 20-5-2016)
+ pcre-8.38-r1653 (upgraded 26-5-2016)
+ form-input-nginx-module (upgraded 20-5-2016)
+ headers-more-nginx-module (upgraded 20-5-2016)
+ echo-nginx-module (upgraded 20-5-2016)
+ ngx_devel_kit (upgraded 10-5-2016)
+ lua-nginx-module (upgraded 21-5-2016)
* prove11 released
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:12 3-5-2016 nginx 1.11.0.1 WhiteKnight

Based on nginx 1.11.0 (27-4-2016) with;
+ stream-lua-nginx-module (upgraded 3-5-2016)
+ Naxsi WAF (upgraded 27-4-2016)
+ lua-nginx-module (upgraded 3-5-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no, openssl fixes
* Additional specifications: see 'Feature list'


10:48 19-4-2016 nginx 1.9.15.1 WhiteKnight

Based on nginx 1.9.15 (15-4-2016) with;
+ HttpSubsModule (upgraded 13-4-2016)
+ pcre-8.38-r1646 (upgraded 13-4-2016)
+ Naxsi WAF (upgraded 13-4-2016)
  conf\naxsi_core.rules updated
* 1.9.14.1 was skipped
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:49 30-3-2016 nginx 1.9.13.2 WhiteKnight

Based on nginx 1.9.13 (30-3-2016) with;
+ Minor core API fixes
+ Naxsi WAF (upgraded 27-3-2016) fully re-engineered
  now includes libinjection and raw_body support
  conf\naxsi_core.rules updated
+ Array-var-nginx-module (upgraded 9-3-2016)
+ lua-nginx-module (upgraded 30-3-2016)
+ pcre-8.38-r1644 (upgraded 9-3-2016)
* stream udp does not yet work
* prove10 released
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


7:40 2-3-2016 nginx 1.9.13.1 WhiteKnight

Shall we raise our swords or shall we raise a drink?
Lets just ride like a WhiteKnight and do better than Red
Red: No one knows what it means, but it's provocative...
nginx: No, it's not, it's gross...
WhiteKnight: ...It gets the people going!
The nginx WhiteKnight release is here!

Based on nginx 1.9.13 (27-2-2016) with;
+ Openssl-1.0.2g (CVE-2016-0800, CVE-2016-0705, CVE-2016-0798,
  CVE-2016-0797, CVE-2016-0799, CVE-2016-0702, CVE-2016-0703,
  CVE-2016-0704)
+ pcre-8.38-r1642 (upgraded 1-3-2016)
+ lua-nginx-module (upgraded 1-3-2016)
* https://www.kb.cert.org/vuls/id/GWAN-A82LHE
* dynamic modules are not supported until proper methods
  for dependencies (including LTS) have been worked out
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no, openssl fixes
* Additional specifications: see 'Feature list'


9:19 22-2-2016 nginx 1.9.12.1 Kitty

Based on nginx 1.9.12 (20-2-2016) with;
+ Openssl-1.0.2f / core fix for SSL_shutdown issue
* prove10 required for 1.9.12 tests
- rdns removed, see https://github.com/openresty/lua-resty-dns
  for a better replacement
* Switched code base for 1.9.12
+ headers-more-nginx-module (upgraded 16-2-2016)
+ echo-nginx-module (upgraded 16-2-2016)
+ set-misc-nginx-module (upgraded 16-2-2016)
+ nginx-auth-ldap (upgraded 7-2-2016)
+ pcre-8.38-r1634 (upgraded 20-2-2016)
+ lua-nginx-module (upgraded 16-2-2016)
+ stream-echo-nginx-module (upgraded 7-2-2016)
+ stream-lua-nginx-module (upgraded 16-2-2016)
+ lua-upstream-nginx-module (upgraded 16-2-2016)
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Kitty series, watch out for the new release name


21:14 28-1-2016 nginx 1.9.11.1 Kitty

Based on nginx 1.9.10 (27-1-2016) with;
+ Openssl-1.0.2f (CVE-2015-3197, CVE-2016-0701)
* CVE-2016-0742, CVE-2016-0746, CVE-2016-0747 can easily be
  mitigated, all resolver fixes have been ported
+ new, stream-lua-nginx-module, experimental
+ stream-echo-nginx-module (upgraded 26-1-2016)
+ nginx-auth-ldap (upgraded 18-1-2016)
* NGINX for Windows is not affected by CVE-2016-1283
* Promoted: GO for Windows (The Go Programming Language)
  Downloads https://golang.org/dl/
  nginx examples https://gist.github.com/hgfischer/7965620
+ SSL_CTX_set_cert_cb() openresty patch
+ Naxsi WAF (upgraded 7-1-2016) #241
+ minor core fixes
* We have removed all old versions from the download section,
  other then LTS versions there is not much point to hang on
  to old versions. If you really are in need of a version that
  has been removed drop us a line
+ lua-nginx-module (upgraded 27-1-2016)
  [C API for the ngx.semaphore]
  [balancer_by_lua]
  [ssl_certificate_by_lua_block]
  [ssl_certifcate_by_lua_file]
  [C API for Lua libraries ngx.ssl and ngx.ocsp]
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


12:11 22-12-2015 nginx 1.9.10.1 Kitty

Based on nginx 1.9.10 (18-12-2015) with;
* Have a great xmas! lets get more NGINX for Windows in 2016!
+ rdns test changes in prove09 (due to core fixes)
+ headers-more-nginx-module (upgraded 18-12-2015)
* preparing for Openssl 1.1.0 (not yet in flr)
+ added proxy(_default).conf file (+renamed fastcgi_default.conf)
  for new installations remove the '_default'
+ lua-nginx-module (upgraded 18-12-2015)
+ pcre-8.38-r1620 (upgraded 8-12-2015)
* Promoted: http://sailorproject.org/ (MVC web framework in Lua)
* new module: nginx-sticky-module, see also our updated manual
  with examples and mixed loadbalance use cases
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


22:21 3-12-2015 nginx 1.9.8.2 Kitty

Based on nginx 1.9.8 (29-11-2015) with;
+ lua-nginx-module (upgraded 2-12-2015)
+ PCRE is now JIT enabled! "Add pcre_jit on; before events {}"
+ pcre-8.38-r1617 (upgraded 3-12-2015)
+ Openssl-1.0.2e (CVE-2015-3193, CVE-2015-3194, CVE-2015-3195,
  CVE-2015-3196)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: no, maintenance release, (h2, openssl fixes)
* Additional specifications: see 'Feature list'


10:12 30-11-2015 nginx 1.9.8.1 Kitty

Based on nginx 1.9.8 (29-11-2015) with;
+ introduced a workaround for broken ajp caching in prove08
+ pcre-8.38-r1613 (upgraded 29-11-2015)
+ added $realip_remote_port variable (like $realip_remote_addr)
+ Fixed an issue(nc) in zlib deflate (ticket #211602127)
+ lua-nginx-module (upgraded 29-11-2015)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:15 6-11-2015 nginx 1.9.7.1 Kitty

Based on nginx 1.9.7 (6-11-2015) with;
+ lua-upstream-nginx-module (upgraded 1-11-2015)
* prove07 required for 1.9.7 upstream tests
+ pcre-8.37b-r1603 (upgraded 1-11-2015)
+ set-misc-nginx-module (upgraded 1-11-2015)
+ Array-var-nginx-module (upgraded 1-11-2015)
+ lua-nginx-module (upgraded 6-11-2015)
+ stream-echo-nginx-module, experimental
  https://github.com/agentzh/stream-echo-nginx-module
+ headers-more-nginx-module (upgraded 1-11-2015)
+ echo-nginx-module (upgraded 1-11-2015)
+ Small changes to 'Tweak-Optimize tcpip' settings file
  server full reboot required after applying changes
  (can be scheduled, no immediate requirement)
* Completed innovative test case, nginx for Windows Lua
  based lawful interception: 5 million concurrent duplicated
  http access and tcp streams simultaneously written and
  analyzed in to SAP EMEA and MongoDB. We're more than ready
  for any Windows Enterprise deployment
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Known broken issues: ajp cache (ajp -without cache- works ok)
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:04 1-10-2015 nginx 1.9.6.1 Kitty

Whats small and slender red and peach, blue eyes, white face with
whiskers, pink bow ? She ain't really that nice, she ain't even
pretty but she gets the job done so here’s Kitty! Remember kids,
as long as it SMELLS like orange juice, you can drink it.
The nginx Kitty release is here!

Based on nginx 1.9.6 (29-9-2015) with;
+ lua-nginx-module v0.9.17 (upgraded 29-9-2015, *_by_lua_block)
+ nginx-module-vts (fix for nginx starttime going haywire)
* prove06 is still being worked on
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Known broken issues: ajp cache
* Scheduled release: no, maintenance release, h2/Lua fixes
* Additional specifications: see 'Feature list'


10:38 21-9-2015 nginx 1.9.5.1 Lizard

Based on nginx 1.9.5 (18-9-2015) with;
* Note about using http2 with plain http,
  https://tools.ietf.org/html/rfc7540#section-3.4
  "This is known to be useful when there is some SSL
  accelerator in place before nginx."
  tnx. to Maxim Dounin for this link and explanation
* prove06 will be released shortly for recent changes
+ spdy replaced with http/2 module (check your .conf file(s))
  selfcheck: https://www.h2check.org/ (which isn't working atm.)
  "listen 443 ssl spdy;" => "listen 443 ssl http2;"
+ lua-nginx-module patches for http/2
+ stream examples:
  load balance your smtp servers stream-smtp-nginx.conf
  load balance your vpn servers stream-openvpn-nginx.conf
+ lua-nginx-module v0.9.17 (upgraded 15-9-2015)
+ mimetype android.package-archive (apk)
+ pcre-8.37b-r1600 (upgraded 6-9-2015)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Known broken issues: ajp cache
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Lizard series, watch out for the new release name


13:03 22-8-2015 nginx 1.9.4.1 Lizard

Based on nginx 1.9.4 (18-8-2015) with;
+ headers-more-nginx-module v0.26 (upgraded 19-8-2015)
+ Openssl-1.0.2d
+ "Proxy-Authenticate" header for the 407 response
+ lua-nginx-module v0.9.16 (upgraded 13-8-2015)
+ pcre-8.37b-r1594 (upgraded 22-8-2015)
+ 'include' in upstream
* Known broken issues: ajp cache, spdy
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


18:54 10-7-2015 nginx 1.9.3.1 Lizard

Based on nginx 1.9.3 (10-7-2015) with;
+ Openssl-1.0.1p (CVE-2015-1793)
+ nginx-module-vts (new fix for 32bit total overflow counters)
+ Array-var-nginx-module v0.04 (upgraded 29-6-2015)
+ echo-nginx-module v0.58 (upgraded 29-6-2015)
+ encrypted-session-nginx-module v0.04 (upgraded 29-6-2015)
+ headers-more-nginx-module v0.26 (upgraded 29-6-2015)
+ lua-nginx-module v0.9.16 (upgraded 29-6-2015)
+ set-misc-nginx-module v0.29 (upgraded 29-6-2015)
+ pcre-8.37b-r1573 (upgraded 29-6-2015, more overflow fixes)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:19 12-6-2015 nginx 1.9.2.1 Lizard

Based on nginx 1.9.2 (9-6-2015) with;
+ Openssl-1.0.1o (upgraded 12-6-2015)
+ Naxsi WAF v0.53-3 (upgraded 12-6-2015)
+ Openssl-1.0.1n (CVE-2015-4000, CVE-2015-1788, CVE-2015-1789,
  CVE-2015-1790, CVE-2015-1792, CVE-2015-1791)
+ pcre-8.37b-r1566 (upgraded 10-6-2015, overflow fixes)
+ nginx-module-vts (fix for 32bit overflow counters including totals)
+ nginx-auth-ldap (upgraded 9-6-2015)
+ nginx-module-vts, fixes for 1.9.1 (upgraded 19-5-2015)
+ LuaJIT-2.0.4 (upgraded 18-5-2015) Tnx to Mike Pall for his hard work!
+ lua51.dll (upgraded 18-5-2015) DO NOT FORGET TO REPLACE THIS FILE !
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


11:16 14-5-2015 nginx 1.9.1.1 Lizard

Based on nginx 1.9.1 (8-5-2015, with 'stream' tcp load balancer) with;
+ pcre-8.37 (upgraded, regression tested)
+ During re-factoring nginx for Windows we've switched code base which
  makes it easier for us to import original nginx code without Windows
  issues by using a new native linux <> windows low level API which 
  natively deals with spinlock, mutex locking, Windows event driven 
  technology and full thread separation
  nginx 1.9 has currently 1 known issue; ajp cache which basically has an
  issue with the 1.7.12 code base caching (without cache ajp works fine)
  https://github.com/yaoweibin/nginx_ajp_module/issues/37
  nb. prove05 will have crashes / failed tests due to this issue
+ 1.9 api change fixes across all modules
- rtmp, 1.7.12.1 is the last free version with rtmp, we do have a rtmp
  special offer for the 1.9 branch (which without rtmp you could use
  to tcp load balance 1.7.12.1 with rtmp)
* 1.7.12 will be kept up to date with critical patches and fixes only,
  no new functions will be added or imported. LTS versions are not affected
* Issues with spdy:
  http://trac.nginx.org/nginx/ticket/714
  http://trac.nginx.org/nginx/ticket/626
  http://trac.nginx.org/nginx/ticket/346
  disable spdy if you have this issue
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This release is dedicated to my beloved wife Shirley Anne aged 57 who
  passed away this May, I shall miss her dearly. After a 40 year relentless
  battle with the effects of diabetes a welsh dragon has lost her fight
  "Mae hen wlad fy nhadau lle rhuo y Dreigiau"


17:02 14-4-2015 nginx 1.7.12.1 Lizard

White Rabbit: We need a lazard with a liddle... a lad... can you help us?
Bill: At your service, gov'nor.
Dodo: Bill, my lad. Have you ever been down a chimney?
Bill: Why, gov'nor, I've been down more chimneys...
Dodo: Excellent, excellent. Now just hop down the chimney and pull that monster out of there.
Bill: Righto, gov'nor... Monster? Aaaaah!
The nginx Lizard release is here!

Based on nginx 1.7.12 (10-4-2015) with;
+ nginx-module-vts (upgraded 10-4-2015)
+ vhts can now display different languages for an outsourced NOC
  see /conf/vhts/vtsvalues-xy.js (default is English)
+ enlarged memory thread work space
+ fixes for fastcgi/proxy cache expire file management
+ imported 3 patches from nginx 1.7.7.1 WhiteRabbit which we thought
  were fixed in the original nginx source tree
+ lua-nginx-module v0.9.16 (upgraded 20-3-2015)
+ Naxsi WAF v0.53-3 (upgraded 20-3-2015)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


20:43 19-3-2015 nginx 1.7.11.3 Gryphon

Based on nginx 1.7.11 (19-3-2015, last changeset 6024:199c0dd313ea) with;
+ Openssl-1.0.1m (CVE-2015-0204, CVE-2015-0286, CVE-2015-0287, CVE-2015-0289,
  CVE-2015-0292, CVE-2015-0293, CVE-2015-0209, CVE-2015-0288)
* In some cases the nginx processes won't stop normally when it's service is
  stopped (workers are still busy), it is advised to add this line:
  TASKKILL /F /IM "nginx*"
  at the end of your 'ngx_stop.cmd' file to make sure no workers are left
  behind before a new master and workers are started
+ Source changes back ported
+ Source changes add-on's: no changes
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: no (openssl fixes)
* Additional specifications: see 'Feature list'
* This is a non scheduled release of the last in the Gryphon series


22:02 14-3-2015 nginx 1.7.11.2 Gryphon

Based on nginx 1.7.11 (14-3-2015, last changeset 6005:d84f0abd4a53) with;
+ nginx-module-vts (Virtual host traffic status)
  adding monitoring for your NOC (network operations center)
  see /conf/vhts
  see our updated 'nginx for Windows - documentation 1.1.pdf' chapter 13
+ set-misc-nginx-module v0.28 (upgraded 10-3-2015)
+ echo-nginx-module v0.57 (upgraded 8-3-2015)
+ lua-nginx-module v0.9.16 (upgraded 10-3-2015)
* nginx for Windows is safe against SSL FREAK attack
+ new best practice ssl_ciphers example (nginx-win.conf)
+ 'include' in upstream http://trac.nginx.org/nginx/ticket/635
+ nginx-auth-ldap (upgraded 2-3-2015)
+ Inter Worker Communication Protocol to support multiple workers with EBLB
  IWCP updated to v0.3 (if you like to keep up to date with IWCP/EBLB for
  other OS's then follow nginx for Windows releases, all Lua code should
  be cross OS compatible)
  see our updated 'nginx for Windows - documentation 1.1.pdf' chapter 10
  with EBLB and IWCP in action, what it can do for you, including examples
+ EBLB (Elastic Backend Load Balancer), see /conf/EBLB
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the Gryphon series, watch out for the new release name


13:31 18-2-2015 nginx 1.7.11.1 Gryphon

Based on nginx 1.7.11 (17-2-2015, last changeset 5984:3f568dd68af1) with;
* Introducing 'nginx for Windows - documentation 1.0', see our new
  documentation repository
* Documentation repository http://nginx-win.ecsds.eu/download/documentation-pdf/
+ Naxsi WAF v0.53-3 (upgraded 16-2-2015)
* See 'ramdisk_setup v3.4.6.exe' on site, speedup your microcache 500x
* (PHP) xcache and (PHP 5.5+) opcache examples in /conf
+ lua-nginx-module v0.9.14 (upgraded 16-2-2015)
* nginx for Windows is not affected by CVE-2015-0235 (Ghost)
+ nginx-auth-ldap (upgraded 22-1-2015)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:14 17-1-2015 nginx 1.7.10.1 Gryphon

Based on nginx 1.7.10 (15-1-2015, last changeset 5964:0a198a517eaf) with;
+ reverted changeset 5962:727177743c3c (causing segfaults)
+ set-misc-nginx-module v0.27 (upgraded 14-1-2015)
+ HttpSubsModule v0.6.4 (upgraded 14-1-2015)
+ lua-nginx-module v0.9.13 (upgraded 14-1-2015)
+ prove05.zip (onsite), a Windows Test_Suite (updated 16-1-2015)
+ See http://nginx-win.ecsds.eu/devtest/EBLB_upstream_dev1.zip for a partly
  working example of managing backends
+ reverted changesets 5960:e9effef98874 and 5959:f7584d7c0ccb (breaks too many
  things, needs re-engineering)
+ Openssl-1.0.1l (CVE-2014-3571, CVE-2015-0206, CVE-2014-3569, CVE-2014-3572, 
  CVE-2015-0204, CVE-2015-0205, CVE-2014-8275, CVE-2014-3570)
+ cache_purge v2.3 (upgraded 30-12-2014)
+ Naxsi WAF v0.53-3 (upgraded 30-12-2014)
+ ngx_signal_process, http://forum.nginx.org/read.php?29,255612
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


12:00 17-12-2014 nginx 1.7.9.1 Gryphon

Based on nginx 1.7.9 (12-12-2014, last changeset 5945:99751fe3bc3b) with;
+ win32 file properties
+ nginx-http-concat v1.2.2 (https://github.com/alibaba/nginx-http-concat)
+ prove04.zip (onsite), a Windows Test_Suite (updated 7-12-2014)
+ cache_purge v2.2 (upgraded 4-12-2014)
+ lua-nginx-module v0.9.13 (upgraded 12-12-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last scheduled release for 2014, have a great xmas and see ya'all in 2015 !


21:38 17-11-2014 nginx 1.7.8.1 Gryphon

Based on nginx 1.7.8 (17-11-2014, last changeset 5904:abb466a57a22) with;
+ Naxsi WAF v0.53-3 (upgraded 15-11-2014)
+ https://github.com/nginx/nginx/pull/7 has been added to code base
  changeset 5900:20d966ad5e89
+ Updated Install_nginx_php_services.zip on site to v1.3
+ Updated, simple Web Application Firewall, see conf/nginx-simple-WAF.conf
+ cache_purge (https://github.com/FRiCKLE/ngx_cache_purge)
+ set-misc-nginx-module v0.26 (upgraded 1-11-2014)
+ lua-nginx-module v0.9.13rc1 (upgraded 15-11-2014)
+ nginx-rtmp-module, v1.1.6 (upgraded 31-10-2014)
+ Re-engineered changeset 5894:1f513d7f1b45
+ Re-engineered changeset 5896:3efdd7788bb0
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


22:55 15-10-2014 nginx 1.7.7.2 Gryphon

Tell me a story and I'll tell you my history. The Mock Turtle and the Gryphon
are here to stay. What! Never heard of uglifying! If you don't know what to
uglify is, you are a simpleton so you'd better get on your way.
The nginx Gryphon release is here!

Based on nginx 1.7.7 (15-10-2014, last changeset 5876:973fded4f461) with;
+ Openssl-1.0.1j (CVE-2014-3513, CVE-2014-3567, SSL 3.0 Fallback protection,
  CVE-2014-3568)
+ lua-nginx-module v0.9.13rc1 (upgraded 15-10-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: no (openssl fixes)
* Additional specifications: see 'Feature list'


11:24 5-10-2014 nginx 1.7.7.1 WhiteRabbit

Based on nginx 1.7.7 (2-10-2014, last changeset 5868:6bbad2e73245) with;
+ pcre-8.36 (upgraded, regression tested)
+ nginx-auth-ldap (upgraded 22-9-2014)
+ nginx-rtmp-module, v1.1.5 (upgraded 22-9-2014)
+ lua-nginx-module v0.9.13 (upgraded 22-9-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the WhiteRabbit series, watch out for the new release name


18:42 15-9-2014 nginx 1.7.5.3 WhiteRabbit

Based on nginx 1.7.5 (15-9-2014, last changeset 5834:ca63fc5ed9b1) with;
+ lua-upstream-nginx-module v0.2 (upgraded 14-9-2014)
+ echo-nginx-module v0.56 (upgraded 14-9-2014)
+ nginx-rtmp-module, v1.1.4 (upgraded 14-9-2014)
  includes https://github.com/arut/nginx-rtmp-module/pull/469
+ lua-nginx-module v0.9.13 (upgraded 14-9-2014)
+ Re-engineered changeset 5820:3377f9459e99, nice try but no sigar
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


22:40 20-8-2014 nginx 1.7.5.2 WhiteRabbit

Based on nginx 1.7.5 (20-8-2014, last changeset 5809:bb26f7ceaaf1) with;
+ ngx_upstream_jdomain (https://github.com/wdaike/ngx_upstream_jdomain)
+ https://github.com/nginx/nginx/pull/7, adding:
  proxy_ssl_client_certificate      cert.pem;
  proxy_ssl_client_certificate_key  cert.key;
  our first multi node cross compiler import !
+ A very simple Web Application Firewall, see conf/nginx-simple-WAF.conf
+ Updated ngxLuaDB to 1.1 (on site !) the drizzle, partial openresty
  and dynamic library / loaded module solution
+ lua-nginx-module v0.9.11 (upgraded 20-8-2014)
+ form-input-nginx-module v0.10 (upgraded 17-8-2014)
+ echo-nginx-module v0.55 (upgraded 19-8-2014)
+ set-misc-nginx-module v0.25 (upgraded 19-8-2014)
+ headers-more-nginx-module v0.25 (upgraded 19-8-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


19:48 7-8-2014 nginx 1.7.5.1 WhiteRabbit

Based on nginx 1.7.5 (7-8-2014, last changeset 5801:ab48149b77a6) with;
+ Openssl-1.0.1i (CVE-2014-3508, CVE-2014-5139, CVE-2014-3509,
  CVE-2014-3505, CVE-2014-3506, CVE-2014-3507, CVE-2014-3510,
  CVE-2014-3511, CVE-2014-3512)
+ lua-nginx-module v0.9.11 (upgraded 6-8-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: no (openssl fixes)
* Additional specifications: see 'Feature list'


19:59 5-8-2014 nginx 1.7.5.0 WhiteRabbit

Based on nginx 1.7.5 (5-8-2014, last changeset 5789:930ce13f19ab) with;
+ nginx fix for CVE-2014-3556
+ lua-nginx-module v0.9.11 (upgraded 30-7-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: no, CVE-2014-3556
* Additional specifications: see 'Feature list'


22:40 26-7-2014 nginx 1.7.4.2 WhiteRabbit

"I'm late! I'm late! For a very important date! No time to say hello,
goodbye! I'm late! I'm late! I'm late!"
The nginx WhiteRabbit release is here!

Based on nginx 1.7.4 (25-7-2014, last changeset 5771:c3b08217f2a2) with;
+ See Install_nginx_php_services.zip on site !
+ set-misc-nginx-module v0.24 (upgraded 26-7-2014)
+ echo-nginx-module v0.54 (upgraded 19-7-2014)
+ lua-nginx-module v0.9.11 (upgraded 25-7-2014)
+ form-input-nginx-module v0.09 (upgraded 23-7-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This release is dedicated to our beloved Yorkshire terrier Peewee who
  aged 11,5 years passed away on Sunday July 20 at 15.15, we shall miss
  him dearly.


15:54 13-7-2014 nginx 1.7.4.1 RedKnight

Based on nginx 1.7.4 (11-7-2014, last changeset 5767:abd460ece11e) with;
+ lua-nginx-module v0.9.11 (upgraded 12-7-2014)
+ echo-nginx-module v0.54 (upgraded 3-7-2014)
+ form-input-nginx-module v0.09 (upgraded 3-7-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'
* This is the last of the RedKnight series, watch out for the new release name


12:37 21-6-2014 nginx 1.7.3.1 RedKnight

Based on nginx 1.7.3 (20-6-2014) with;
+ new best practice ssl_ciphers example (nginx-win.conf)
+ fastcgi/upstream fix: http://forum.nginx.org/read.php?29,250947,251007#msg-251007
+ form-input-nginx-module (https://github.com/calio/form-input-nginx-module)
+ Naxsi WAF conf\naxsi_core.rules updated 15-6-2014; File uploads: 1500-1600
+ nginx-auth-ldap (upgraded 12-6-2014)
+ lua-nginx-module v0.9.9 (upgraded 16-6-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: yes
* Additional specifications: see 'Feature list'


20:13 5-6-2014 nginx 1.7.2.2 RedKnight

Based on nginx 1.7.2 (5-6-2014) with;
+ Openssl-1.0.1h (CVE-2014-0224, CVE-2014-0221, CVE-2014-0195,
  CVE-2014-0198, CVE-2010-5298, CVE-2014-3470)
+ New nginx Windows icon
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Scheduled release: no (openssl fixes)
* Additional specifications: see 'Feature list'


14:53 1-6-2014 nginx 1.7.2.1 RedKnight

Based on nginx 1.7.2 (30-5-2014) with;
+ optimization registry file renamed
+ FD table size increased to allow more sustained power with a single worker
+ original nginx:syslog support
+ RFC 6302 EU-SP legislation log source ports: 
  use $remote_addr:$remote_port when using log_format
+ lua-nginx-module v0.9.8 (upgraded 1-6-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


17:21 17-5-2014 nginx 1.7.1.3 RedKnight

Go ask Alice, I think she'll know, When logic and proportion have
fallen dead And the white knight is talking backwards And the red
queen's lost her head Remember what the dormouse said Feed your head,
feed your head, as the RedKnight rizes again from the dead !
The nginx RedKnight release is here /->
             ,      ,  /
        ____/~\    ~O
    ,;~( )_  )'' /~()'-{---
       )/  |(     /~)
       ~    ~     ~ ~
     Phil/sb/Donovan/mbfh

Based on nginx 1.7.1 (16-5-2014) with;
+ Openssl fix for out-of-bounds write in SSL_get_shared_ciphers (#3317)
+ integration of Mercurial and Git into our crosscompiler
  this reduces diff sets import and cross checks from 12 to 1 hour
+ lua-nginx-module v0.9.7 (upgraded 15-5-2014)
+ Select-boost is out of beta and is now the default
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


13:56 2-5-2014 nginx 1.7.1.2 Snowman

Based on nginx 1.7.1 (30-4-2014) with;
+ lua-nginx-module v0.9.7 (upgraded 1-5-2014)
+ Openssl fix for CVE-2010-5298
+ AJP tomcat backend support (https://github.com/yaoweibin/nginx_ajp_module)
  Note: a folder '.\nginx\ajp_temp' will be created, when running nginx jailed
  create it yourself and set additional rights for the service user who runs
  nginx to allow access
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


21:28 24-4-2014 nginx 1.7.1.1 Snowman

Based on nginx 1.7.1 (24-4-2014) with;
+ lua-upstream-nginx-module v0.1 (upgraded 24-4-2014)
+ Streaming with nginx-rtmp-module, v1.1.4 (upgraded 24-4-2014)
+ New development tree nginx export 1.7
+ Naxsi WAF v0.53-1 (upgraded 17-4-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


23:55 12-4-2014 nginx 1.5.14.1 Snowman

Based on nginx 1.5.14 (11-4-2014) with;
+ echo-nginx-module v0.53 (upgraded 12-4-2014)
+ Should I upgrade? (Upgrade Assessment Matrix)
+ lua-nginx-module v0.9.7 (upgraded 11-4-2014)
+ Streaming with nginx-rtmp-module, v1.1.4 (upgraded 11-4-2014)
+ set-misc-nginx-module (upgraded 11-4-2014)
+ RDNS (https://github.com/flant/nginx-http-rdns) (upgraded 11-4-2014, it's back!)
+ pcre-8.35 (upgraded)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications: see 'Feature list'


CVE-2014-0160 (heartbleed / heartbeat) statement: as of version 'nginx 1.5.13.2 Snowman'
nginx for Windows is not affected by CVE-2014-0160, this version uses openssl-1.0.1g, any
previous version can be vulnerable.


10:30 8-4-2014 nginx 1.5.13.2 Snowman

Based on nginx 1.5.13 (8-4-2014) with;
+ CVE fix CVE-2014-0160
+ openssl-1.0.1g (upgraded 8-4-2014)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications are like 0:18 5-4-2014 nginx 1.5.13.1 Snowman


0:18 5-4-2014 nginx 1.5.13.1 Snowman

.-= This Is Snowman =-.
Here's a little snowman fast and fat, here's it's power as fast as a cat
When you run Windows you can hear it shout, take me in try me out!
The nginx Snowman release is here!

Based on nginx 1.5.13 (3-4-2014) with;
+ A fix for ssl_session_cache via trac ticket #528, thanks to Maxim!
+ Stability fixes, more performance tuning
+ multiple workers now use an api (efficiency and control)
+ Streaming with nginx-rtmp-module, v1.1.4 (upgraded 3-4-2014)
+ Naxsi WAF v0.53-1 (upgraded 3-4-2014, conf\naxsi_core.rules id 15+16)
+ LuaJIT-2.0.3 (upgraded 31-3-2014) Tnx to Mike Pall for his hard work!
+ lua51.dll (upgraded 31-3-2014) DO NOT FORGET TO REPLACE THIS FILE !
+ lua-nginx-module v0.9.7 (upgraded 3-4-2014)
+ FAQ included in archive
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications are like 20:29 18-3-2014 nginx 1.5.12.2 Cheshire


20:29 18-3-2014 nginx 1.5.12.2 Cheshire

Based on nginx 1.5.12 (release 18-3-2014) with;
+ nginx security advisory (CVE-2014-0133)
+ echo-nginx-module v0.51 (upgraded 18-3-2014)
+ Nginx-limit-traffic-rate-module (https://github.com/bigplum/Nginx-limit-traffic-rate-module)
+ lua-nginx-module v0.9.6 (upgraded 18-3-2014)
+ changed compile order (openresty)
+ Source changes back ported
+ Source changes add-on's back ported
+ Changes for nginx_basic: Source changes back ported
* Additional specifications are like 13:58 9-3-2014 nginx 1.5.12.1 Cheshire


13:58 9-3-2014 nginx 1.5.12.1 Cheshire

Based on nginx 1.5.12 (9-3-2014) with;
+ Fixed a c99 logging issue in naxsi
+ Now includes nginx_basic. Need a simple powerful Windows webserver without all the
  bling of it's big brother ? then nginx_basic is for you, other custom builds are
  available upon request
+ nginx security advisory (CVE-2014-0088)
+ encrypted-session-nginx-module (https://github.com/agentzh/encrypted-session-nginx-module)
+ Fully ASLR and DEP compliant for shared memory (ea. limit_conn_zone, limit_req_zone, etc.)
+ lua-upstream-nginx-module (https://github.com/agentzh/lua-upstream-nginx-module)
+ lua-nginx-module v0.9.5rc2 (upgraded 8-3-2014)
+ Streaming with nginx-rtmp-module, v1.1.3 (upgraded 8-3-2014)
+ echo-nginx-module v0.51 (upgraded 21-2-2014)
+ headers-more-nginx-module v0.25 (upgraded 17-1-2014)
+ nginx-auth-ldap (upgraded 21-2-2014)
+ HttpSubsModule (upgraded 21-2-2014)
+ Additional custom 503 error handler via 513 (see onsite readme for example)
  Issue: a "return 503" can only be used once in a location block, when a custom 503
         is used for example with limit_req_zone you can't have a second custom 503
	 for a maintenance page
  example:
    server {
        listen  80;
        server_name  www.any.nl;
        root    '/webroot/www.any.nl';
        error_page 503 @floodnotice;
        error_page 513 @maintenance;
        location / {
            if (-f $document_root/maintenance_mode.html) { return 513; }
            # Or with a local IP check
            ## Note: there is a bug with this last IF, see http://forum.nginx.org/read.php?2,251650
            ## for more info about this incorrect behavior (dd. 12-7-2014)
            # set $maintmode S; if ($remote_addr ~ "^(10.10.*.*)$") { set $maintmode L; }
            # if (-f $document_root/maintenance_mode.html) { set $maintmode "${maintmode}M"; }
            # if ($maintmode = SM) { return 513; }
            # Yes we all know by now, ifisevil so put a sock in it
            # Or with pure Lua, no IF issues
            ## rewrite_by_lua '
            ##   local s = 0; local v = 0;
            ##   local source_fname = ngx.var.document_root .. "/maintenance_mode.html";
            ##   local file = io.open(source_fname);
            ##   if file then v=1; file:close(); end;
            ##   if string.find(ngx.var.remote_addr, "^10.10.30.") then v=0; end;
            ##   if v>0 then return ngx.exit(513); end;
            ## ';
            try_files $uri $uri/ =404;
            index  index.html index.htm;
            limit_req zone=floodh burst=32 nodelay;
            # generates a 503 when triggered
            # see limit_req_zone directive how limit_req works
        }
        location @floodnotice {
            root html
            rewrite ^ /floodnotice.html break;
        }
        location @maintenance {
            rewrite ^ /maintenance_mode.html break;
            # process a 513 but return a 503 to client !
        }
    }
  The normal behavior would be (if the file exists) to return the contents 
  of "/maintenance_mode.html" with a "HTTP/1.1 200 OK", or when the 503 error_page
  is used a 503, however a 503 is often used for other things, With this new 513
  error_page the same thing can be done but the 513 is replaced with a 503 when
  the headers are compiled which allows you to use the real 503 for other things
+ Select-boost: event driven, non-blocking API select() replacement, Beta
  No need to enable anything, it is fully automatic and won't be used if certain
  conditions do not pass internal tests
+ Source changes back ported
+ Source changes add-on's back ported
* Additional specifications are like 14:05 10-1-2014: nginx 1.5.9.1 Cheshire


14:05 10-1-2014: nginx 1.5.9.1 Cheshire

When she sleeps she gently purrs, you hardly know she's there, but when she wakes
you're gonna hear her roar. nginx Cheshire release is here !
This native build runs on Windows XP SP3 and higher, both 32 and 64 bit.

Based on nginx 1.5.9 (4-1-2014) with;
+ changed compile order
+ prove01.zip (onsite), a Windows Test_Suite way to show/prove it all really works
+ ngx_http_auth_ldap2 (experimental, https://github.com/kvspb/nginx-auth-ldap)
  follow examples on github site, not the site example in example.conf, this is an
  experimental build addition ! (when not used it won't affect anything else)
+ set-misc-nginx-module (https://github.com/agentzh/set-misc-nginx-module)
+ headers-more-nginx-module (https://github.com/agentzh/headers-more-nginx-module)
+ openssl-1.0.1f (upgraded 8-1-2014)
+ lua-nginx-module v0.9.4 (upgraded 9-1-2014)
+ Streaming with nginx-rtmp-module, v1.1.1 (upgraded 10-1-2014)
+ echo-nginx-module v0.50 (upgraded 8-1-2014)
- RDNS has been removed until a blocking issue has been resolved
+ added http_auth_request_module
+ Source changes back ported
+ Source changes add-on's back ported
* Additional specifications are like 19:46 18-12-2013: nginx 1.5.8.3 Caterpillar


19:46 18-12-2013: nginx 1.5.8.3 Caterpillar

Based on nginx 1.5.8 (release) with;
+ prove.zip (onsite), a Windows Test_Suite way to show/prove it all really works
  with at the moment a limited amount of tests which will grow over time
+ Streaming with nginx-rtmp-module, v1.0.8 (upgraded 16-12)
+ pcre-8.34 (upgraded)
+ lua-nginx-module v0.9.3 (upgraded)
+ echo-nginx-module v0.50 (upgraded)
+ Source changes back ported (including fixes for the changed resolver API)
+ Source changes add-on's back ported (including fixes for the changed resolver API)
* More compiler optimizations
* Additional specifications are like 15:34 6-12-2013: nginx 1.5.8.2 Caterpillar


15:34 6-12-2013: nginx 1.5.8.2 Caterpillar

Based on nginx 1.5.8 (5-12-2013) with;
+ Fix for nginx -t 'Assertion failed' issue
+ HttpSubsModule (https://github.com/yaoweibin/ngx_http_substitutions_filter_module)
+ echo-nginx-module (https://github.com/agentzh/echo-nginx-module)
+ ngx_http_lower_upper_case (https://github.com/replay/ngx_http_lower_upper_case)
+ Naxsi WAF (Web Application Firewall) v0.53-1 (upgraded 5-12-2013)
+ lua-nginx-module v0.9.2 (upgraded 6-12)
+ Streaming with nginx-rtmp-module, v1.0.8 (upgraded 6-12)
+ Source changes back ported
+ Source changes add-on's back ported
* The debug version is no longer needed, Intel static profiler data is used
  nginx crash info/logging or event dump info is all that is needed
* Intel static profiler "the need for speed" compiler optimization
* Additional specifications are like 19:18 30-11-2013: nginx 1.5.8.1 Caterpillar


19:18 30-11-2013: nginx 1.5.8.1 Caterpillar

Based on nginx 1.5.8 (29-11-2013) with (mainly bugfixes in add-on's);
+ Naxsi WAF (Web Application Firewall) v0.53-1 (upgraded)
+ lua-nginx-module v0.9.2 (upgraded 30-11)
+ Streaming with nginx-rtmp-module, v1.0.8 (upgraded 29-11)
+ Source changes back ported
+ Source changes add-on's back ported
* Additional specifications are like 20:32 19-11-2013: nginx 1.5.7.2 Caterpillar


20:32 19-11-2013: nginx 1.5.7.2 Caterpillar

Based on nginx 1.5.7 (19-11-2013) with;
+ nginx fix for CVE-2013-4547 (nginx 1.5.7.1 Caterpillar removed from download)
+ Source changes back ported
+ Simplified new installations
* Additional specifications are like 12:22 16-11-2013: nginx 1.5.7.1 Caterpillar


12:22 16-11-2013: nginx 1.5.7.1 Caterpillar

The nginx 'Caterpillar' is a "you are no longer in Kansas Alice" *MONSTER* release bringing
to Windows full scalability with multiple workers!
This native build runs on Windows XP SP3 and higher, both 32 and 64 bit.

Based on nginx 1.5.7 (9-11-2013 + spdy hang fix) with;
+ A solution for the multiple worker(shm_) issue, commercially sponsored solution by ITPP
  with a HUGE thanks to Vittorio Francesco Digilio from Italy for his relentless debugging,
  analysis and solution !
+ Naxsi WAF (Web Application Firewall) v0.53 (https://github.com/nbs-system/naxsi)
  see https://github.com/nbs-system/naxsi/wiki how to use it and also see the conf/ folder
+ lua-nginx-module v0.9.2 (upgraded)
+ Streaming with nginx-rtmp-module, v1.0.6 (http://nginx-rtmp.blogspot.nl/) (upgraded)
* Additional specifications are like 12:38 2-10-2013: nginx 1.5.6.4 Butterfly


12:38 2-10-2013: nginx 1.5.6.4 Butterfly

The Nginx 'Butterfly' release brings to Windows stable and unleashed power of Nginx, Lua, 
Streaming feature, Reverse DNS, SPDY, easy c250k in a non-blocking and event driven build 
which runs on Windows XP SP3 or higher, both 32 and 64 bit.

Based on nginx 1.5.6 (release) with;
+ RDNS (https://github.com/flant/nginx-http-rdns)
+ Array-var-nginx-module (https://github.com/agentzh/array-var-nginx-module)
+ ngx_devel_kit v0.2.19
+ lua-nginx-module v0.9.0
* Additional specifications are like 13:46 25-9-2013: nginx 1.5.6.3 Alice


13:46 25-9-2013: nginx 1.5.6.3 Alice

Based on nginx 1.5.6 (25-9-2013) with;
+ Bug fixes in lua-nginx-module(master 25-9-2013) and ngx_devel_kit(master 25-9-2013) by agentzh
+ Both debug and non-debug versions, the non-debug version is production use ready ! 
* vcredist_x86 is required, get it here (http://www.microsoft.com/en-us/download/details.aspx?id=5555)
* Additional specifications are like 10:37 23-9-2013: nginx 1.5.6.1 Alice
* 1.5.6.2 was skipped for public release


10:37 23-9-2013: nginx 1.5.6.1 Alice

Based on nginx 1.5.6 (22-9-2013) with;
+ Streaming with nginx-rtmp-module, v1.0.4 (http://nginx-rtmp.blogspot.nl/)
+ lua-nginx-module v0.8.9 (tnx to agentzh about precompiled headers!)
+ LuaJIT-2.0.2 => (lua51.dll include / lua51.lib build)
+ Added lua51.dll (is required)
+ ngx_devel_kit v0.2.15
* Additional specifications are like 10:27 10-9-2013: B02 build


10:27 10-9-2013: B02 build

Based on nginx 1.4.2 with;
  pcre-8.32
  zlib-1.2.8
  openssl-1.0.1e
+ Compiled with: FD_SETSIZE = 16384 (original Windows source files modified)
+ Now capable to handle C250K ! (with optimization registry file)
+ Added Windows optimization registry file, check your current values BEFORE setting the new ones
+ Added debug symbols file (let us know where it went wrong when you have a crash)
+ Added adjusted nginx(-win).conf for Windows
+ Added SPDY
* Runs on Windows XP SP3 or higher, both 32 and 64 bit
* Set priority to High for both nginx.exe processes
* When nginx is running as a service: My computer -> Properties -> Advanced -> Performance -> 
  Advanced -> Processor scheduling, Adjust for best performance set to background services
* Website created for easy download: http://nginx-win.ecsds.eu/


				  DISCLAIMER

Use of this program acknowledges this disclaimer of warranty:
"This program is supplied as is. The author(s) and associated companies disclaims all warranties,
express or implied, including, without limitation, the warranties of merchantability and of fitness
of this program for any purpose. The author(s) and associated companies assumes no liability for
damages direct or consequential, which may result from the use of or inability to use this program.
Even if author(s) and associated companies has been advised of the possibility of such damages or
any claim by any other party."
