// User authentication
FirebaseAuth mAuth = FirebaseAuth.getInstance();
FirebaseUser currentUser = mAuth.getCurrentUser();

// Real-time messaging with FCM
FirebaseMessaging.getInstance().subscribeToTopic("chat");

// Database integration (Firebase Realtime Database)
DatabaseReference databaseReference = FirebaseDatabase.getInstance().getReference("messages");

// Sending a message
String messageText = "Hello, World!";
Message message = new Message(currentUser.getUid(), messageText);
databaseReference.push().setValue(message);

// Receiving messages
databaseReference.addChildEventListener(new ChildEventListener() {
    @Override
    public void onChildAdded(@NonNull DataSnapshot snapshot, @Nullable String previousChildName) {
        Message receivedMessage = snapshot.getValue(Message.class);
        // Handle the received message
    }

    // Other methods for handling data changes
});

// Message class
public class Message {
    private String senderId;
    private String text;

    // Constructor, getters, and setters
}
