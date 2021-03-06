# Config Keystone


# MỤC LỤC




Tham khảo: https://docs.openstack.org/ocata/config-reference/identity.html  
Config Keystone trong file `/etc/keystone/keystone.conf`  
\- In the `[database]` section, configure database access:  
```
[database]
# ...
connection = mysql+pymysql://keystone:KEYSTONE_DBPASS@controller/keystone
```

Replace `KEYSTONE_DBPASS` with the password you chose for the database.

>Note  
Comment out or remove any other connection options in the [database] section.

\- In the [token] section, configure the Fernet token provider:  
```
[token]
# ...
provider = fernet
```

Bạn có thể thế fernet bởi `uuid`, `pki` hoặc `pkiz`.  

\- Trên là các attribute bắt buộc phải cấu hình, ngoài ra bạn có thể cấu hình tham các attribute:  
- số key tối đa dùng cho fernet (max_active_key)
- hạn sử dụng của một token (expiration_time)
- Time to cache identity data (cache_time) , ví dụ sử dụng horizon để truy cập openstack, thì cache_time là thuộc tính chỉ định thời gian lưu trữ token trong cache của web brower.
- Time to cache the revocation list and the revocation events (revocation_cache_time)
- Cấu hình access Keystone sử dụng ssl.


















