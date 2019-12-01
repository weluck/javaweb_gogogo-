5. HttpSession原理（理解）
  * request.getSession()方法：
    > 获取Cookie中的JSESSIONID：
      <> 如果sessionId不存在，创建session，把session保存起来，把新创建的sessionId保存到Cookie中
      <> 如果sessionId存在，通过sessionId查找session对象，如果没有查找到，创建session，把session保存起来，把新创建的sessionId保存到Cookie中
      <> 如果sessionId存在，通过sessionId查找到了session对象，那么就不会再创建session对象了。
      <> 返回session
    > 如果创建了新的session，浏览器会得到一个包含了sessionId的Cookie，这个Cookie的生命为-1，即只在浏览器内存中存在，如果不关闭浏览器，那么Cookie就一直存在。
    > 下次请求时，再次执行request.getSession()方法时，因为可以通过Cookie中的sessionId找到session对象，所以与上一次请求使用的是同一session对象。
 
  * 服务器不会马上给你创建session，在第一次获取session时，才会创建！request.getSession();

  * request.getSession(false)、request.getSession(true)、request.getSession()，后两个方法效果相同，
    > 第一个方法：如果session缓存中(如果cookie不存在)，不存在session，那么返回null，而不会创建session对象。

6. HttpSession其他方法：
  * String getId()：获取sessionId；
  * int getMaxInactiveInterval()：获取session可以的最大不活动时间（秒），默认为30分钟。当session在30分钟内没有使用，那么Tomcat会在session池中移除这个session；
  * void invalidate()：让session失效！调用这个方法会被session失效，当session失效后，客户端再次请求，服务器会给客户端创建一个新的session，并在响应中给客户端新session的sessionId；
  * boolean isNew()：查看session是否为新。当客户端第一次请求时，服务器为客户端创建session，但这时服务器还没有响应客户端，也就是还没有把sessionId响应给客户端时，这时session的状态为新。
