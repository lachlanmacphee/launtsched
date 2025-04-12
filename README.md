# Launtsched

## What is this?

[Benjamin Dopplinger](https://github.com/benasocj) first started this repo as a way to be able to schedule pausing and unpausing his [Launtel](https://launtel.net.au) internet service through a simple Python script.

[Lachlan MacPhee](https://github.com/lachlanmacphee) (me) became the maintainer of this repo in 2025 as Ben had moved on from using Launtel as his ISP and was busy with other things. I was interested in adding some functionality for changing speed plans and handling multiple services through the one script.

## How do I use this?

Run this command and then fill in your Launtel username and password in the newly created `.env` file.

```sh
cp .env.example .env
```

Create a Python `venv` (virtual environment) and install the requirements from `requirements.txt` using `pip` or similar.

Run the Python script with the `pause`, `unpause` or `plan` argument, such as:

```sh
python3 change_service_status.py pause
```

If you already know the `id` of the service you want to `pause`, `unpause`, or edit the `plan` for, you can choose that service directly using the `service_id` flag:

```sh
python3 change_service_status.py plan --service_id 123456
```

## How do you schedule this?

You can run a free Linux Compute Engine instance on Google Cloud Platform and use the `at` command to schedule the execution of the script at a certain time.

For example, to pause your service at 9pm run the following:

```sh
echo 'python3 launtel_change_service_status.py pause'|at 9pm
```

Or to schedule an unpause for a future date::

```sh
echo 'python3 launtel_change_service_status.py unpause'|at 0:05am 2021-01-01
```

## Be kind and considerate to Launtel

Knowing that NBN's turn around times can be fairly slow when pausing/unpausing a service, Launtel would still have to pay for an extra day if you pause your service at 11:59 pm but it only gets paused on NBN's side after midnight. Hence,if you know you'll be in bed by 9 pm then [love your neighbour as yourself](https://www.esv.org/mark12:31/) and be kind to Launtel by scheduling the pausing of your service for that time in order to give Launtel a chance to still finish the pausing process within the same day so they don't have to pay the extra.
