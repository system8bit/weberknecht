weberknecht - Java WebSocket Client Library
===========================================

Weberknecht is a Java implementation of the client side of the WebSocket Protocol for use in Java applications.

Requirements
------------
 * Apache Commons Codec 1.6

Usage
-----
This short code snippet shows how to integrate weberknecht in your application:

```java
try {
    URI url = new URI("ws://127.0.0.1:8080/test");
    WebSocket websocket = new WebSocket(url);
		
    // Register Event Handlers
    websocket.setEventHandler(new WebSocketEventHandler() {
            public void onOpen()
            {
                System.out.println("--open");
            }
								
            public void onMessage(WebSocketMessage message)
            {
                System.out.println("--received message: " + message.getText());
            }
								
            public void onClose()
            {
                System.out.println("--close");
            }

            public void onPing() {}
            public void onPong() {}
        });
		
    // Establish WebSocket Connection
    websocket.connect();
		
    // Send UTF-8 Text
    websocket.send("hello world");
		
    // Close WebSocket Connection
    websocket.close();
}
catch (WebSocketException wse) {
    wse.printStackTrace();
}
catch (URISyntaxException use) {
    use.printStackTrace();
}
```
