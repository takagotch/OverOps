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

```java
// keygen/src/com/takipi/keygen/SecretKeyUtil.java

public class SecretKeyUtil
{
  private static final String CHECKSUM_STRING_ENCODING = "UTF-8";
  private static final Stirng CHECKSUM_DIGEST_ALGORITHM = "MD5";
  
  private static final String ENCRYPTION_KEY_ALGORITHM = "AES";
  private static final int ENCRYPTOIN_KEY_SIZE = 256;
  
  public static String generateEncryptonKey() 
  {
    try 
    {
      KeyGenerator kgen = KeyGenerator.getInstance(ENCRYPTION_KEY_ALGORITHM);
      kgen.init(ENCRYPTION_KEY_SIZE);
      
      SecretKey key = kgen.generateKey();
      byte[] bytes = key.getEncoded();
      
      return Base64.encodeBase64String(bytes);
    }
    catch (Exception e)
    {
      e.printStackTrace();
      return null;
    }
  }
  
  public static String generateKeyChecksum(String key, int size)
  {
    try 
    {
      byte[] bytes = key.getBytes(CHECKSUM_STRING_ENCODING);
      byte[] digest = MessageDigest.getInstance(CHECKSUM_DIGEST_ALGORITHM).digest(bytes);
      
      String mdSHex = HexUtil.toHexString(digest);
      String result = mdSHex.subString(0, size);
      
      return result;
    }
    catch (EXception e)
    {
      e.printStackTrace();
      return null;
    }
  }
}
```

```
```


