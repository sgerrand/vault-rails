# Vault Rails Changelog

## v0.3.1 (March 3, 2017)

IMPROVEMENTS

- Add ability to lazy decrypt attributes [GH-41]

## v0.3.0 (August 21, 2016)

IMPROVEMENTS

- Add support for Rail 5 and better testing matrix

BUG FIXES

- Use a pre-configured client to ensure options are inherited from the
  default client

## v0.2.0 (May 2, 2016)

BREAKING CHANGES
- The API for configuration now lives under `Vault::Rails` instead of `Vault`.
  Existing users will need to update their configuration as follows:

  ```diff
  - Vault.configure do |config|
  + Vault::Rails.configure do |config|
  ```
- Remove testing mode and use an in-memory vault store in development and test
  instead with the option to disable
- Load from Vault during initialize and save instead of on each change. This is
  not necessarily a "breaking" change, but users who were depending on the
  previous behavior of always making a call to Vault when setting attributes
  will experience a break. However, the new approach significantly reduces the
  load on the Vault cluster.

IMPROVEMENTS

- Allow specifying custom serialization options
- Add dirty tracking for Active Record models
- Unset instance variables when `reload` is called for ActiveRecord models
- Fix issues that would occur when using multiple threads
- Add support for retries

BUG FIXES

- Update documentation to better describe configuration options
- Update documentation around advanced configuration options
- Update documentation to include example Vault policies for the transit backend
- Do not attempt to read back a secret after writing to the logical backend
- Increase test coverage
- Force character encodings

## v0.1.2 (May 14, 2015)

- Do not automatically mount or create keys (security issue, see README for
  more information)
- Add testing harness

## v0.1.1 (May 13, 2015)

- Lazy-connect to Vault - this fixes a bug which would require users to run a
  local Vault installation just to get the Rails application to boot.

## v0.1.0 (April 29, 2015)

- Initial release
