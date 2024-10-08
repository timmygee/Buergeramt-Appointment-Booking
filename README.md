# Bürgeramt Appointment Booking

> Note that this is not an officially supported script.

If you need an appointment at Berlin's Bürgeramt (citizen's office), you have to be quick and patient. This Python script books you the next available appointment at a Bürgeramt.
In order not to refresh pages by hand for hours and then be too slow in the appointment selection I wrote this little helper script.


## Getting started
Make sure Python is installed on your System:
```
python --version
```

Install dependencies:
```
pip install -r requirements.txt
```


## How to use
```
py booking.py --name "John Doe" --email "j.doe@example.com" --phone "01234567890" --id "121151"
```

`--name` - Enter the first and last name of the person for whom the appointment is booked
`--email` - Enter the e-mail address to which the appointment confirmation should be sent
`--phone` - Enter your phone number
`--id` - Enter the ID of the service you want to book an appointment for, e.g. "121151" to apply for a passport.
To find the matching ID, click on a service at [https://service.berlin.de/dienstleistungen/](https://service.berlin.de/dienstleistungen/). The number at the end of the URL is the ID. This script is not suitable for services that can be done online.
`--start_date` - [optional, format "DD.MM.YYYY", default is the current date] Add the first date from which an appointment booking should be made. For example, today is August 8. Your appointment should not take place before August 12. Enter `--start_date 12.08.2023` in the command to make sure that a free appointment is not booked on e.g. August 9.
`--end_date` - [optional, format "DD.MM.YYYY", default is no end date] Add the last date on which an appointment booking should be made.


## Good to know

### Booking process

When a booking is successful, a verification code is sent to the email address provided. This code must be entered on the booking page to confirm the appointment. The script will wait for the code to be entered and then confirm the appointment. If the code is not entered within a certain time, you will fail to secure the appointment.

### Timeout: Too many attempts
The script tries to book an appointment until it is successful. This can take many attempts at times. Note that there is a security mechanism on the booking page that will timeout you for a short time if too many attempts have been made. In this case it would make sense to use VPN and change the location if necessary.


---
Developed by [Peter R. Stuhlmann](https://peter-stuhlmann-webentwicklung.de).
Licensed under the [MIT license](./LICENSE).