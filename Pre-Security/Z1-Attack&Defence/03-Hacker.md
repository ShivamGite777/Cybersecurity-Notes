### Offensive Security

Offensive Security means **proactively testing systems to find security weaknesses** before real attackers find them.
Ethical hacking must always be done with **permission** and within the defined **scope**.

##  Key Terms

 **Red Teaming** → Simulates a real attack to test security defenses.
 **Penetration Testing** → Authorized testing to find and exploit vulnerabilities.
 **Vulnerability** → A weakness in a system that can be abused.
 **Exploit** → A method used to take advantage of a vulnerability.
 **Scope** → Defines what you are allowed and not allowed to test.

# Practical: Finding Hidden Web Pages

### Scenario

Mike wants to launch his online shop safely. We need to check if any **hidden or unintended pages** are publicly accessible.

<img width="991" height="852" alt="image" src="https://github.com/user-attachments/assets/657907f7-9059-4695-9846-d7be34795393" />
<img width="991" height="852" alt="image" src="https://github.com/user-attachments/assets/657907f7-9059-4695-9846-d7be34795393" />
Example:

```text
http://www.onlineshop.thm/
``` 
### Exploiting Weaknesses & Dictionary Attack

## Chaining Weaknesses

A single weakness may not be dangerous, but multiple weaknesses can be **combined** to create a serious security risk.

### Example:

```text
Hidden Login Page
      ↓
Weak Password
      ↓
Admin Login
      ↓
Access Protected Information
```

 **Think of vulnerabilities like dominoes:** one weakness can trigger another.

## Think Like a Hacker

Ethical hackers should:

   Ask: **What if this doesn't work as intended?**
   Test unexpected inputs and actions
   Chain small weaknesses together
   Think like an attacker
  Always test with proper authorization


##  Why Are Credentials Valuable?

Valid credentials can provide access to:

 **Sensitive functionality** → Restricted features
 **User data** → Names, emails, account details
 **Administrative features** → User/settings management
 **Further attack opportunities** → Discover more vulnerabilities


##  Hydra — Dictionary Attack

Instead of testing passwords manually, **Hydra** can automate login attempts using a wordlist.

```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```
## The Complete Attack Chain
1. Find hidden /login page
          ↓
2. Discover username: admin
          ↓
3. Test common passwords
          ↓
4. Find weak admin password
          ↓
5. Log in successfully
          ↓
6. Access protected area
## Weak Password Testing

Known username:

```text
admin
```

Example password list:

```text
abc123
123456
password
qwerty
654321
```

The correct password discovered was:

```text
qwerty
```

After logging in:

```text
THM{born_to_hack!}
```
<img width="981" height="873" alt="image" src="https://github.com/user-attachments/assets/11796476-e44a-4365-97a1-ca162a582b0c" />
<img width="1018" height="877" alt="image" src="https://github.com/user-attachments/assets/cc783328-cd3c-4b05-8f7a-ecde743f5292" />


### Command Breakdown

| Option               | Meaning                                      |
| -------------------- | -------------------------------------------- |
| `hydra`              | Password-testing tool                        |
| `-l admin`           | Username = `admin`                           |
| `-P passlist.txt`    | Password wordlist                            |
| `www.onlineshop.thm` | Target website                               |
| `http-post-form`     | HTTP POST login form                         |
| `/login`             | Login page                                   |
| `^USER^`             | Username placeholder                         |
| `^PASS^`             | Password placeholder                         |
| `F=incorrect`        | Marks login as failed if `incorrect` appears |
| `-V`                 | Shows each attempt                           |

