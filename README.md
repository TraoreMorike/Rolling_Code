**Remote Sender and Receiver**

This code implements a remote sender and receiver system using Linear Feedback Shift Registers (LFSRs) and Advanced Encryption Standard (AES) encryption. The system generates rolling codes, tokens, and verifies the authenticity of messages.

**Components**

* `RemoteSender`: Initializes an LFSR with a given serial number, taps, initial state, and number of bits. Generates rolling code values and tokens.
* `Receiver`: Initializes an LFSR with the same parameters as the sender. Generates rolling code windows and verifies the authenticity of received messages.

**Usage**

1. Define the master key (a 16-byte hexadecimal string). This key is used to generate the sender key.
2. Create a receiver object using the master key, taps, initial state, and number of bits.
3. Generate the initial rolling code window for the receiver.
4. Use the receiver's serial number to generate the sender key using the KDF (Key Derivation Function).
5. Create a sender object using the receiver's serial number, sender key, taps, initial state, and number of bits.
6. Generate the initial rolling code window for the sender.
7. Extract the raw token from the sender's rolling code window and encrypt it using AES to generate the token.
8. Send the message (serial number + token) to the receiver.

**Verification**

1. The receiver generates its own token using the encrypted message and the master key.
2. Compare the receiver's token with the original token sent by the sender. If they match, the message is verified as authentic.

**Notes**

* This code assumes a valid pairing between the remote sender and the receiver.
* The sender and receiver must share the same taps, initial state, and number of bits for the LFSR.
* The master key should be kept secret in real-life situations.

**License**

This code is licensed under the MIT License.
