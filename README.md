**Voice Chat Application Report**

**Introduction**

This report presents the development of a **Voice Chat Application** as part of the **CS447 Computer Networks** course. This project aims to provide users with a user-friendly voice communication platform where they can connect to a server, create rooms, and join conversations in real time.

**Objectives**

The main objective of this project is to design and implement a voice chat application that meets the following requirements:

*   Simple and user-friendly interface.
*   Real-time voice communication.
*   The ability for users to create or join chat rooms.

**Technologies Used**

The application was implemented with the **Python programming language**, utilizing the following libraries:

*   **socket** for networking.
*   **pyaudio** for audio streaming.
*   **threading** for handling multiple concurrent operations.

Additionally, an **AWS EC2 instance** was used for server hosting.

**Architecture**

The Voice Chat Application follows a **client-server model**:

*   **Server:** Manages connections, handles chat room creation and closure, and broadcasts audio data to connected clients.
*   **Client:** Connects to the server, streams audio, and handles incoming audio data with necessary implementations.

**Workflow**

1.  The client establishes a **connection to the server** using a socket.
2.  Users can **create new rooms** or **join existing rooms**.
3.  Audio is **captured and streamed to the server** in chunks using **pyaudio**.
4.  The server **broadcasts the audio data** to other participants in the same room.
5.  The client **processes and plays the received audio** in real time.

**Implementation Details**

**Client Code Highlights**

**Server Connection:**

*   The client establishes a connection to the server and retrieves a welcome message.

**Output Stream Management:**

*   Ensures proper audio playback configuration and initializes necessary threads for each user.

**Audio Streaming:**

*   The client captures audio from the microphone using the **pyaudio** library.
*   Audio data is sent to the server in chunks and played back through the speakers.

**Threading:**

*   Separate threads manage audio sending, receiving, and user input to ensure **real-time operation**.


**Jitter Buffer**

*   Implemented using a **deque-based jitter buffer**.
*   Stores and processes audio chunks to ensure **smooth audio playback** by storing chunks up until some threshold which was 2 in our case.
*   Prevents **audio stuttering** caused by network jitter.
*   Ensures smooth audio playback by injecting silence when no audio chunks are available in the buffer. This prevents playback from stalling or introducing delays caused by waiting for incoming data, maintaining a consistent and uninterrupted audio stream.
*   Incoming audio data is managed by the parse\_server\_messages function.

**GUI Implementation**

The GUI provides a **user-friendly interface** for interacting with the application.

**Room Creation:**

*   Users can create a room by typing NEW:<RoomName> into the input bar.

**Room Joining:**

*   Users can join an existing room from the list displayed in the GUI.

**Leave Room:**

*   Users can leave a room by typing leave into the bar and pressing Enter.

**Concurrent Audio Handling**

*   Each user's audio stream is managed in a **separate playback thread**.
*   Ensures seamless communication without blocking other audio streams.

**Server Implementation**

**Client Connection Management:**

*   The server accepts incoming client connections and assigns them to threads.

**Room Management and Handling New Connections:**

*   Manages client connections, displays available rooms, and handles room creation.

**Audio Broadcasting:**

*   Audio data from one client is broadcasted to all other clients in the same room.

**Challenges and Solutions**

**Audio Latency:**

*   **Challenge:** Latency in audio transmission caused noticeable delays.
*   **Solution:** Implemented a **jitter buffer** to balance and smooth audio playback.

**Server Load Management:**

*   **Challenge:** High server load during simultaneous audio streams.
*   **Solution:** Used **efficient threading** and **socket programming** to optimize performance.

**Results**

*   **Audio Quality:** Clear and uninterrupted for up to 5 users.
*   **Latency:** Acceptable latency (100-150 ms) under normal network conditions.
*   **Room Management:** Users can create and join rooms without issues.

**Conclusion and Future Work**

The **Voice Chat Application** successfully achieved its objectives. Users can now connect, create rooms, and communicate in real-time.

**Future Improvements:**

*   **Scalability:** Optimize the server for higher user loads.
*   **Encryption:** Implement secure communication channels.
*   **Enhanced GUI:** Improve the user interface for better usability.

This project offered practical experience in socket programming, audio processing, and real-time communication systems, greatly enhancing our understanding of computer networks.

**Contributers**

Ahmet Berkay Arslanpençe

Eren Darak

Ömer Emre Bozkurt

Ragıp Şamil Bekiryazıcı

Kerem Okumuş

Git-Hub link for the project: [OmerEmreBozkurt/VoiceChatApp: Voice Chat Application for CS447 - GitHub](https://github.com/OmerEmreBozkurt/VoiceChatApp)
