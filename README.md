# bot
-EBUILD telegram-cli-9999.ebuild 665 SHA256 446cf5cd54f60485dda2f47e5c027b78f182053ef88cd09d7327603e2d5f3d86 SHA512 8a3673de91ec60e89391956523a4b61872161a23a7e0babdbd90cbdd8602104ba1855d09bd0af1d2092890eb202f498750610bf71e3bd0562e37ec984deb333e WHIRLPOOL e943b8870f461c62e3dc7f061dcad264c25758d1d50a0c34f5232d3be6ae26e9dd2ca1289e65b6153ff5b8800194969f1c53e3adc81aa4e47bf25c2f7e6aab7c
function save_config( )
-  serialize_to_file(_config, './bot/config.lua')
-  print ('saved config into ./bot/config.lua')
+  serialize_to_file(_config, './data/config.lua')
+  print ('saved config into ./data/config.lua')
 end
 
 
 function load_config( )
-  local f = io.open('./bot/config.lua', "r")
+  local f = io.open('./data/config.lua', "r")
   -- If config.lua doesnt exists
   if not f then
-    print ("Created new config file: bot/config.lua")
+    print ("Created new config file: data/config.lua")
     create_config()
+  else
+    f:close()
   end
-  f:close()
-  local config = loadfile ("./bot/config.lua")()
+  local config = loadfile ("./data/config.lua")()
   for v,user in pairs(config.sudo_users) do
     print("Allowed user: " .. user)
   end
 @@ -159,8 +160,8 @@ function create_config( )
       "youtube" },
     sudo_users = {our_id}  
   }
-  serialize_to_file(config, './bot/config.lua')
-  print ('saved config into ./bot/config.lua')
+  serialize_to_file(config, './data/config.lua')
+  print ('saved config into ./data/config.lua')
 end
 
 function on_our_id (id)
