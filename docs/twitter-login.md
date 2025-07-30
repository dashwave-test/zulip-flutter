# Twitter Login (experimental)

This document describes how to enable and configure Twitter login for the Zulip Flutter app.

## Enabling the Twitter Login Button

The Twitter login button is hidden by default. To enable it for testing and development purposes, you can set the `enableTwitterLogin` flag to `true` in the `GetServerSettingsResult` object returned by the server.

This is intended for development and testing only. In a production environment, the visibility of the Twitter login button should be controlled by the server configuration.

## Server-Side Configuration

For the Twitter login to be fully functional, the Zulip server must be configured to support Twitter as a social authentication backend. This is done by leveraging the `python-social-auth` library that is used by the Zulip server.

The high-level steps for configuring the server are:

1.  **Install the necessary `python-social-auth` backend for Twitter.**
    The Zulip server documentation provides guidance on how to add new authentication backends. You will need to add the Twitter backend to your Zulip server's Python environment.

2.  **Configure the Twitter authentication backend in your Zulip server's settings.**
    This involves adding a new entry to the `AUTHENTICATION_BACKENDS` setting in `/etc/zulip/settings.py` and providing the necessary Twitter API credentials (API key and secret) in `/etc/zulip/zulip-secrets.conf`.

3.  **The Zulip server will then advertise the Twitter authentication method to clients.**
    Once the server is correctly configured, it will include the Twitter authentication method in the response to the `/api/v1/server_settings` endpoint. The Zulip Flutter app will then automatically display the Twitter login button on the login page.

For detailed instructions on how to configure social authentication backends on the Zulip server, please refer to the official Zulip server documentation.
