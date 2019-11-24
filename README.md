# SMTP Relay to GMAIL

# What is postfix-gmail?

It is a simple Postfix SMTP server that relay all messages to GMAIL 


# How to use this image

## running a instance

    docker run --rm -p 30025:25 -d --name postfix \
    -e GMAIL_USER=AAAAAAAAAAAAAAAAAAAAAAAA \
    -e GMAIL_PASS=BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB \
    fametec/postfix-gmail:latest

## ... or via docker-compose

    version: '3.2'
    #
    ### Services
    #
    services:
    #
    # GMAIL
    #
      relay:
        image: fametec/postfix-gmail:latest
        restart: unless-stopped
        container_name: relay-gmail
        ports:
         - "30025:25"
        environment:
         SES_USER: XXXXXXXXXXXXXXXX
         SES_PASS: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
         

# testing

    echo "Email Test" | mail -s "This is a simple test" contato@fametec.com.br
 
or

    sendmail -f sender@example.com recipient@example.com
    From: Sender Name <sender@example.com>
    Subject: Simple Test                
    This message was sent using GMAIL.                
    .


