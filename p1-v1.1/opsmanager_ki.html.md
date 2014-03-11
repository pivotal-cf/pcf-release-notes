---
title: Pivotal Ops Manager 1.1.0.0 Known Issues
---
* Deleting products in Ops Manager must be done separately from applying changes or installing other products to avoid unexpected errors.

* After installing the 'Pivotal Metrics' product (currently in Beta), operators must increase the Collector VM instance count to 1 and re-push Elastic Runtime to have the setting take effect.

* Deleting a product that provides a service broker to Elastic Runtime (e.g. HD, MySQL) leaves orphan rows in the Cloud Controller DB. Contact Pivotal Support for more information.

- If you are upgrading from Ops Manager 1.0.0.1 to Ops Manager 1.1.0.0, follow these steps to upgrade the Developer Console:
    1. Login to the Ops Manager VM using SSH. The username is `tempest`. You set the password during the .ova deployment into vCenter.
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

