# Pi-init
Raspberry Pi security improving


## OS update
    sudo apt update
    sudo apt full-upgrade

## 2FA SSH (Google Two-Factor Authenticator)
### Installation
    sudo apt install libpam-google-authenticator
    google-authenticator

### Configuration
Modify the lines in `/etc/pam.d/sshd`

    # @include common-auth
    auth required pam_google_authenticator.so

Modify the lines in `/etc/ssh/sshd_config`

    ChallengeResponseAuthentication yes
    UsePAM yes
    AuthenticationMethods publickey,keyboard-interactive
    PasswordAuthentication no
    
Restart to take effect

    sudo systemctl restart sshd
