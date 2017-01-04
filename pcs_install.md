## Getting Started with PCS

- create a folder ~/pcs_root *** make it a symlink
- in ~/pcs_root clone each of the bitbucket repos (except for website)
- brew install tmux
- gem install tmuxinator
- brew install openssl
- gem install eventmachine -v 1.0.8 -- --with-cppflags=-I/usr/local/opt/openssl/include
- brew install nginx
- mkdir -p keys/ssl/
- generate a ssl certificate and rename 'star_armakuni_co_uk.chained.cert'
'star_armakuni_co_uk.key' for the cert and key



- `export PATH=$PATH:$(pwd)/bin` - from pcs-tool  then run bundle

- `git clone git@bitbucket.org:pcs-uk/pcs-applicant-ui.git pcs-applicant-app`
