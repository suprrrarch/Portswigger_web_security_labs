
Ways of injecting OS commands

You can use a number of shell metacharacters to perform OS command injection attacks.

A number of characters function as command separators, allowing commands to be chained together. The following command separators work on both Windows and Unix-based systems:

 &
 &&
 |
 ||

The following command separators work only on Unix-based systems:

;

Newline (0x0a or \n)

On Unix-based systems, you can also use backticks or the dollar character to perform inline execution of an injected command within the original command:

`

injected command `

$(

injected command )

The different shell metacharacters have subtly different behaviors that might change whether they work in certain situations. This could impact whether they allow in-band retrieval of command output or are useful only for blind exploitation.

Sometimes, the input that you control appears within quotation marks in the original command. In this situation, you need to terminate the quoted context (using “ or ‘) before using suitable shell metacharacters to inject a new command.

How to prevent OS command injection attacks

The most effective way to prevent OS command injection vulnerabilities is to never call out to OS commands from application-layer code. In almost all cases, there are different ways to implement the required functionality using safer platform APIs.

If you have to call out to OS commands with user-supplied input, then you must perform strong input validation. Some examples of effective validation include:

    · Validating against a whitelist of permitted values.

    · Validating that the input is a number.

    · Validating that the input contains only alphanumeric characters, no other syntax or whitespace.

Never attempt to sanitize input by escaping shell metacharacters. In practice, this is just too error-prone and vulnerable to being bypassed by a skilled attacker.
