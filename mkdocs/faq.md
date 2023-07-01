# &#128587;&#8205;&#9794;&#65039; FAQ

## General

#### I've found the Cat and I like it very much, but I'm not able to follow your instructions to install it on my machine. Can you help?

The Cheshire Cat is a framework to help developers to build vertical AIs: you will need some basic technical skills to follow our instructions.
Please try to ask in the support channel in our discord server, and remember this is all volunteers effort: be kind! :)

#### Why the Cat does not default to some open LLM instead of ChatGPT or GPT-3?

Our intention is not to depend on any specific LLM: the Cat does not have a preference about which LLM to use. Nonetheless, at the moment, OpenAI tools still provide the best results for your bucks.
Decision is up to you.

#### Are text and documents sent to the Cat safe and not shared with anybody?

Well, the local memory is safe and under your control, although embeddings and prompts are shared with your configured LLM, meaning you need to check how safe is the LLM.
We plan to adopt local LLMs, at which point all your data will be under your control.

## Basic Info

#### Can I insert a long article into the chat?

Please avoid pasting long articles into the chat.  
Use Rabbit Hole to upload long texts instead: just click on the attachment icon in the chat input widget and upload your file.

#### Are the configured LLM APIs used to "instruct" the Cat with the documents I'm going to upload?

That's not exactly how it works: basically when you ask something to the Cat, we pass to the configured LLM a prompt with your actual question + data that can be useful to answer that question. Data can be parts of your documents or chat history.  
Please check our documentation for more details about how the Cat works for you.

#### Can I talk to the Cat in a language different from English?

Of course you can: just change the prompts in the Plugin folder accordingly, and take care not to mix languages to get best results.

#### How can I know where the Cat gets the answers? I'd like to know if it's using the files I uploaded or if it's querying the configured LLM.

Just open the console in your browser to check the logs there. At some point soon, this information will end up in the user interface, but at the moment is behind the scenes.

#### I sent to the Cat some text and documents I won't to get rid of, How can I do?

You can delete the `long_term_memory` folder and restart the Cat!

## Errors

#### Why am I getting the error `RateLimitError` in my browser console?

Please check if you have a valid credit card connected or if you have used up all the credits of your OpenAI trial period.

#### Everything works in localhost but not on another server

You should configure ports in the `.env` file. Change according to your preferred host and ports:

```text
# Decide host and port for your Cat. Default will be localhost:1865
CORE_HOST=anotherhost.com
CORE_PORT=9000
```

#### Docker has no permissions to write

This is a matter with your docker installation or the user you run docker from.

#### The Cat seems not to be working from inside a Virtual Machine

In VirtualBox you can select Settings->Network, then choose NAT in the "Attached to" drop down menu. Select "Advanced" to configure the port forwarding rules. Assuming the guest IP of your VM is 10.0.2.15 (the default) and the ports configred in the .env files are the defaults, you have to set at least the following rule:

| Rule name | Protocol | Host IP     | Host Port | Guest IP   | Guest Port |
|-----------|----------|-------------|-----------|------------|------------|
| Rule 1    | TCP      | 127.0.0.1   | 1865      | 10.0.2.15  | 1865       |

If you want to work on the documentation of the Cat, you also have to add one rule for port 8000 which is used by `mkdocs`, and to configure `mkdocs` itself to respond to all requests (not only localhost as per the default).  

## Customization

#### I want to build my own plugin for the Cat: what should I know about licensing?

Plugins are any license you wish, you can also sell them.
The Cat core is GPL3, meaning you are free to fork and go on your own, but you are forced to open source changes to the core.

#### Port 1865 is allowed by my operating system and/or firewall

Change the port as you wish in the `.env` file.

```text
# Decide host and port for your Cat. Default will be localhost:1865
CORE_HOST=localhost
CORE_PORT=9000
```
