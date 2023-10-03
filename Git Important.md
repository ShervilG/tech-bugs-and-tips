#git #github #ssh
# SSH Keys
GitHub public key and your local private key are not used in conjunction to encrypt commits. Their roles are different in the SSH authentication process.
Here's how it works:
1. **Authentication**: When you interact with a GitHub repository over SSH, your local private key and the GitHub public key are used for authentication. Your local private key is used to prove your identity to GitHub, while GitHub's public key is used to confirm the authenticity of GitHub's server. Once authenticated, GitHub knows who you are.
2. **Encryption**: Git uses a separate set of keys for encryption. Git uses symmetric encryption for data transfer between your local machine and the remote repository, and this encryption is negotiated during the SSH handshake. The data is encrypted and decrypted on both ends using a shared session key, which is established during the SSH connection setup.    
So, your local private key and the GitHub public key are primarily used for authentication, not for encrypting the content of your commits. The encryption of the commit data happens separately through the Git protocol and SSH encryption.
