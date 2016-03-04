---
title: Pivotal Dev Console v.1.1.0.0 Known Issues
owner: Apps Manager
---

- There are several bugs related to using Dev Console with the Admin user that Ops Manager creates. Pivotal recommends that users create a new user with admin privileges, using the cf command line tools, and log in to Dev Console using that user.

- The `system` org is reserved for the Developer Console. Spaces cannot be created in the `system` org.

- cf cli v6.0.1, included with the Developer Console in PCF v1.1, has a bug that prevents Windows users from pushing archived apps like zips, jars, wars, etc. v6.0.2 has the fix. You can download it here: [https://console.run.pivotal.io/tools](https://console.run.pivotal.io/tools).

- If you are upgrading from Ops Manager 1.0.0.1 to Ops Manager 1.1.0.0, follow these steps to upgrade the Developer Console:
    1. Log in to the Ops Manager VM using SSH. The username is `tempest`. You set the password during the .ova deployment into vCenter.
    1. Replace `/var/tempest/app_metadata/console.yml` with the contents below.
    1. Restart the VM.
    1. In Ops Manager, click **Apply Changes**.


```yaml

---
name: console
product_version: 1.1.0.0
metadata_version: 1.0
source:
  name: console
  version: "ccbd61"
  file: console-source-ccbd61.zip
  md5: be78e8f09ca3bb796e67a7f89e7030e3

manifest: |
  mem: 1G
  disk: 1G

  path: "<%= app_sources_dir %>/<%= source_file %>"

  applications:
  - name: console
    host: none
    domain: none
    instances: 1
    command: bundle exec rake db:migrate db:seed server:start_command
  - name: console-scheduler
    host: none
    domain: none
    instances: 1
    command: bundle exec rake scheduler:start
  - name: console-workers
    host: none
    domain: none
    instances: 2
    command: bundle exec rake workers:start_command

  services:
    authentication:
      label: user-provided
      credentials:
        CF_CLIENT_ID: portal
        CF_CLIENT_SECRET: <%= console_uaa_client_secret %>
        CF_LOGIN_SERVER_URL: <%= cf_address_provider.login_url %>
        CF_UAA_SERVER_URL: <%= cf_address_provider.uaa_url %>
  <% if console_db_property_typed_value("smtp_address").not_empty? %>
    smtp:
      label: user-provided
      credentials: <%= smtp_credentials %>
  <% end %>

  env:
    RAILS_ENV: production
    RACK_ENV: production
    BUNDLE_WITHOUT: test:development
    DATABASE_URL: <%= database_url %>
    ON_PREMISE: "true"
    VERIFY_SSL: "false"
    SECRET_TOKEN: <%= secret_token %>
    CF_CC_API_URL: <%= cf_address_provider.system_api_url %>
    CF_CONSOLE_URL: <%= cf_address_provider.console_url %>
    DEFAULT_REPLY_TO: <%= console_reply_to %>
    DEFAULT_FROM: <%= console_from %>

```


