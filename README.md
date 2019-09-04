### overops
---
https://github.com/takipi

https://www.overops.com/

```java
// keygen/src/com/takipi/keygen/key/SecretKeyGenerator.java

public class SecretKeyGenerator
{
  private static final String KEY_DELIM = "#";
  
  private static final int CHECKSUM_SIZE = 4;
  
  public static String generateKey(String keyPrefix)
  {
    StringBuilder sb = new StringBuilder();
    
    String encryptionKey = SecretKeyUtil.generateEncryptionKey();
    
    sb.append(keyPrefix);
    sb.append(KEY_DELIM);
    sb.append(encryptionKey);
    
    String keyChecksum = SecretKeyUtil.generateKeychecksum(sb.toString(), CHECKSUM_SIZE);
    
    sb.append(KEY_DELIM);
    sb.append(keyChecksum);
    
    return sb.toString();
  }
}

```

```
```

```
```


