# Jegarn Android SDK

android implementation of jegarn client.




## Install


update your build.gradle file.

    dependencies {
        compile project(':jegarn')
    }




## Example

connect

    String host = "jegarn.com";
    int port = 9501;
    int reconnectInterval = 5000;
    String account = "test";
    String password = "test";
    // is connect to ssl server ?
    boolean enableSsl = true;
    DefaultListener listener = new DefaultListener();
    JegarnManager.getInstance().init(host,port, reconnectInterval, account, password, enableSsl,listener);
    JegarnManager.getInstance().run();

and new message listener of chat packet

    JegarnManager.client.getChatManager().addListener(new ChatManagerListener() {
        @Override
        public boolean processPacket(Chat packet) {
            if (toUserUid.equals(packet.getFrom())) {
                if (packet instanceof TextChat) {
                    TextChat pkt = (TextChat) packet;
                }
            }
            return true;
        }
    });

send new message

    TextChat packet = new TextChat("my_uid", "friend_uid", TextChat.TYPE, new TextChatContent("hello"));
    JegarnManager.client.sendPacket(packet);



## License

[Apache License Version 2.0](./LICENSE)