# webfinger.sh
Bash Shell implementation of webfinger (RFC7033) client

# implementation
This utility has been implemented along side the [swicg / activitypub-webfinger](https://swicg.github.io/activitypub-webfinger/) standard document in order for testing and compliance.

# Instillation
The only file required is `webfinger` it is self installing, installing `curl` and `jq` if not already installed, requiring super user `sudo` password.
JRD Schema validation if used will also require either Python and PIP, or Node.js and NPM, installing `check-jsonschema` or `ajs-cli` and `ajv-formats` respectively.

# Usage

```
Usage: ./webfinger
    [ -r <rel> | --rel <rel> | --REL <rel> ]
    [ -V | --validate ]
    [ -M | --mastodon ]
    [ -v | --verbose ]
    [ -f | --fake ]
    <user@domain>
```
## --verbose | -v
Provides infromation about execuation steps and variables.
## --fake | -f
Do not perform the curl HTTP REST GET call to `https://<server>/.well-known/webfinger&resource=<resource>`
## --rel \<rel\> | --REL \<rel\> | -r \<rel\>
set the vale of rel in curl call `https://<server>/.well-known/webfinger&resource=<resource>&rel=<rel>`
## --mastadon | -M
perform MORE restrictive Mastodon checking on the `username` rather than using RFC7033 checking.
## --validate | -V
validate the returned JRD (JSON Resource Descriptor) against a JRD Schema.

# Example usage

## basic normal usage
`webfinger AaronNGray@fosstodon.org`

## Mastodon usage
`webfinger -M AaronNGray@fosstodon.org`

## validation
`webfinger -V AaronNGray@fosstodon.org`

## test usage
`webfinger -vf AaronNGray@fosstodon.org`

## rel usage
`webfinger --rel self AaronNGray@fosstodon.org`
