# Create a localhost tunnel



In order to test an application running on localhost. It can be very useful to create a public link to localhost. That is easily done with Ngrok. SImply go to their website, signup and follow their instructions https://ngrok.com/

https://dashboard.ngrok.com/get-started/setup

To create a tunnel write this command in the terminal

```
ngrok http PORT_NUMBER
```

Where `PORT_NUMBER` needs to be replaced with the port number your application has