---
id: index
title: Introduction
slug: /sdks
---

In order to connect your application to Unleash you will need a client SDK (software developer kit) for your programming language and an [API token](../user_guide/api-token). The SDK will handle connecting to the Unleash server instance and retrieving feature toggles based on your configuration. All versions of Unleash (OSS, Pro, and Enterprise) use the same client SDKs.

Unleash provides official client SDKs for a number of programming language. Additionally, our community have developed and contributed SDKs for other languages. So if you can't find your favorite language in the list of official SDKs, check out the [list of clients written by our fantastic community](#community-sdks).

## Official SDKs

### Server-side SDKs:

Server-side clients run on your server and communicate directly with your Unleash instance. We provide these official clients:

- [Go SDK](/sdks/go_sdk)
- [Java SDK](/sdks/java_sdk)
- [Node.js SDK](/sdks/node_sdk)
- [PHP SDK](/sdks/php_sdk)
- [Python SDK](/sdks/python_sdk)
- [Ruby SDK](/sdks/ruby_sdk)
- [Rust SDK](https://github.com/unleash/unleash-client-rust)
- [.NET SDK](/sdks/dot_net_sdk)

### Front-end SDKs

For security and performance reasons, the front-end SDKs do not communicate directly with your Unleash instance. Instead, they go via the [Unleash Proxy](unleash-proxy.md).

- [Android SDK](/sdks/android_proxy_sdk)
- [iOS Proxy SDK](/sdks/proxy-ios)
- [Javascript SDK](/sdks/proxy-javascript)
- [React Proxy SDK](/sdks/proxy-react)


### Server-side SDK compatibility table

The below table shows what features the various server-side SDKs support. Note that certain features make sense only for some clients due to how the programming language works or due to how the client works.

**Legend**:

- ✅: Implemented
- ⭕: Not yet implemented, but we're looking into it
- ❌: Not implemented, not planned
- **N/A**: Not applicable to this SDK

:::note
If you see an item marked with a ❌ that you would find useful, feel free to reach out to us ([on Slack](https://join.slack.com/t/unleash-community/shared_invite/zt-8b6l1uut-LL67kLpIXm9bcN3~6RVaRQ), for instance) with your use case. It may not be something we can prioritize right now, but if you'd like to contribute it back to the community, we'd love to help you build it.
:::


| Capability                                                                                        | [Java](/sdks/java_sdk) | [Node.js](/sdks/node_sdk) | [Go](/sdks/go_sdk) | [Python](/sdks/python_sdk) | [Ruby](/sdks/ruby_sdk) | [.NET](/sdks/dot_net_sdk) | [PHP](/sdks/php_sdk) | [Rust](https://github.com/unleash/unleash-client-rust) | [Unleash Proxy](unleash-proxy.md) |
|---------------------------------------------------------------------------------------------------|:----------------------:|:-------------------------:|:------------------:|:--------------------------:|:----------------------:|:-------------------------:|:--------------------:|:------------------------------------------------------:|:----------------------------------------:|
| **Category: Initialization**                                                                      |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Async initialization                                                                              | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     | N/A                                      |
| Can block until synchronized                                                                      | ✅                     | ✅                        | ⭕                 | ⭕                         | ⭕                     | ✅                        | ⭕                   | ⭕                                                     | N/A                                      |
| Default refresh interval                                                                          | 10s                    | 15s                       | 15s                | 15s                        | 15s                    | 30s                       | 30s                  | 15s                                                    | 5s                                       |
| Default metrics interval                                                                          | 60s                    | 60s                       | 60s                | 60s                        | 60s                    | 60s                       | 30s                  | 15s                                                    | 30s                                      |
| Context provider                                                                                  | ✅                     | N/A                       | N/A                | N/A                        | N/A                    | ✅                        | ✅                   | N/A                                                    | N/A                                      |
| Global fallback function                                                                          | ✅                     | ✅                        | ✅                 | ✅                         | ❌                     | ❌                        | ❌                   | ❌                                                     | N/A                                      |
| Toggle Query: `namePrefix`                                                                        | ✅                     | ✅                        | ❌                 | ❌                         | ❌                     | ❌                        | ❌                   | ❌                                                     |                                          |
| Toggle Query: `tags`                                                                              | ✅                     | ✅                        | ❌                 | ❌                         | ❌                     | ❌                        | ❌                   | ❌                                                     |                                          |
| Toggle Query: `project_name`                                                                      | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | N/A                  | ⭕                                                     |                                          |
| **Category: Custom Headers**                                                                      |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| static                                                                                            | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ⭕                                                     | N/A                                      |
| function                                                                                          | ✅                     | ✅                        | ⭕                 | ✅                         | ⭕                     | ✅                        | ⭕                   | ⭕                                                     | N/A                                      |
| **Category: Built-in strategies**                                                                 |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| [Standard](../user_guide/activation_strategy#standard)                                            | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| [Gradual rollout](../user_guide/activation_strategy#gradual-rollout)                              | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| [Gradual rollout: custom stickiness](../user_guide/activation_strategy#customize-stickiness-beta) | ✅                     | ✅                        | ⭕                 | ✅                         | ✅                     | ✅                        | ✅                   | ⭕                                                     |                                          |
| [UserID](../user_guide/activation_strategy#userids)                                               | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| [IP](../user_guide/activation_strategy#ips)                                                       | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| [IP](../user_guide/activation_strategy#ips): CIDR syntax                                          | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ⭕                        | ⭕                   | ✅                                                     |                                          |
| [Hostname](../user_guide/activation_strategy#hostnames)                                           | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| **Category: [Custom strategies](../advanced/custom_activation_strategy)**                         |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Basic support                                                                                     | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| **Category: [Strategy constraints](../advanced/strategy_constraints)**                            |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Basic support (`IN`, `NOT_IN` operators)                                                          | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| **Category: [Unleash Context](../user_guide/unleash_context)**                                    |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Static fields (`environment`, `appName`)                                                          | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Defined fields                                                                                    | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Custom properties                                                                                 | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| **Category: [`isEnabled`](../client-specification#implementation-of-isenabled)**                  |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Can take context                                                                                  | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Override fallback value                                                                           | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Fallback function                                                                                 | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ⭕                        | ⭕                   | ⭕                                                     |                                          |
| **Category: [Variants](../advanced/toggle_variants)**                                             |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Basic support                                                                                     | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Custom fallback variant                                                                           | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ⭕                                                     |                                          |
| Custom weight                                                                                     | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ⭕                                                     |                                          |
| [Custom stickiness (beta)](../advanced/stickiness#custom-stickiness-beta)                         | ✅                     | ✅                        | ⭕                 | ✅                         | ✅                     | ✅                        | ✅                   | ⭕                                                     |                                          |
| **Category: Local backup**                                                                        |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| File based backup                                                                                 | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ⭕                                                     |                                          |
| **Category: Usage metrics**                                                                       |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Can disable metrics                                                                               | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Client registration                                                                               | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| Basic usage metrics (yes/no)                                                                      | ✅                     | ✅                        | ✅                 | ✅                         | ✅                     | ✅                        | ✅                   | ✅                                                     |                                          |
| [Impression data](../advanced/impression-data.md)                                                 | ⭕                     | ⭕                        | ⭕                 | ⭕                         | ⭕                     | ⭕                        | ⭕                   | ⭕                                                     | N/A                                         |
| **Category: Bootstrap (beta)**                                                                    |                        |                           |                    |                            |                        |                           |                      |                                                        |                                          |
| Bootstrap from file                                                                               | ✅                     | ✅                        | ⭕                 | ⭕                         | ✅                     | ⭕                        | ⭕                   | ⭕                                                     | ✅                                        |
| Custom Bootstrap implementation                                                                   | ✅                     | ✅                        | ⭕                 | ⭕                         | ✅                     | ⭕                        | ⭕                   | ⭕                                                     | ✅                                        |

## Community SDKs ❤️ {#community-sdks}

Here's some of the fantastic work our community has done to make Unleash work in even more contexts. If you still can't find your favorite language, let us know and we'd love to help you create the client for it!

- [afontaine/unleash_ex](https://gitlab.com/afontaine/unleash_ex) (Elixir)
- [AppsFlyer/clojure-unleash](https://github.com/AppsFlyer/unleash-client-clojure) (Clojure)
- [aruizs/unleash-client-cpp](https://github.com/aruizs/unleash-client-cpp) (C++)
- [mikefrancis/laravel-unleash](https://github.com/mikefrancis/laravel-unleash) (Laravel - PHP)
- [minds/unleash-client-php](https://gitlab.com/minds/unleash-client-php) (PHP)
- [ngx-unleash-proxy-client](https://github.com/snowfrogdev/snowfrogdev/tree/main/packages/ngx-unleash-proxy-client) (Angular - TypeScript)
- [pmb0/nestjs-unleash](https://github.com/pmb0/nestjs-unleash) (NestJS - Node.js)
- [silvercar/unleash-client-kotlin](https://github.com/silvercar/unleash-client-kotlin) (Kotlin)
- [Stogon/unleash-bundle](https://git.stogon.io/Stogon/unleash-bundle/) (PHP - Symfony)
- [uekoetter.dev/unleash-client-dart](https://pub.dev/packages/unleash) (Dart)
- _...your implementation for your favorite language._

## Implement your own SDK {#implement-your-own-sdk}

If you can't find an SDK that fits your need, you can also develop your own SDK. To make implementation easier, check out these resources:

- [Unleash Client Specifications](https://github.com/Unleash/client-specification) - Used by all official SDKs to make sure they behave correctly across different language implementations. This lets us verify that a gradual rollout to 10% of the users would affect the same users regardless of which SDK you're using.
- [Client SDK overview](../client-specification) - A brief, overall guide of the _Unleash Architecture_ and important aspects of the SDK role in it all.
