# 应用场景

我们在实际编程中，API返回的数据可能并不是JSON等对机器友好的格式，而可能是纯文本等需要API用户自己提取信息的格式，这就需要正则表达式(Regular Expression)来提取信息。

例：以下有两段精简过的E-mail头文件信息，包括了一系列我们想获得的信息，若是想用普通方法提取信息，则需要对每一条规则独立编写，而正则表达是可以免除这种无意义的重复工作。

    Date: Sat, 5 Jan 2008 09:12:18 -0500
    To: source@collab.sakaiproject.org
    From: stephen.marquard@uct.ac.za
    Subject: [sakai] svn commit: r39772 - content/branches/sakai_2-5-x/content-impl/impl/src/java/org/sakaiproject/content/impl

    Date: Fri, 4 Jan 2008 18:08:57 -0500
    To: source@collab.sakaiproject.org
    From: louis@media.berkeley.edu
    Subject: [sakai] svn commit: r39771 - in bspace/site-manage/sakai_2-4-x/site-manage-tool/tool/src: bundle java/org/sakaiproject/site/tool

# 实际例子

## Example 1 -- 获取邮件头文件中的发件人地址
Patten:

    "From: (.*)"

Output:

    ['stephen.marquard@uct.ac.za', 'louis@media.berkeley.edu']

Explanation

    "From\
    : (.*)"
    "From: " 即匹配原文中的 "From: "，
    "." 匹配任意字符，除 '\n' 外，
    "*" 匹配前面的子表达式零次或多次，在此处为匹配 "." 即任意字符零次或多次，
    "(pattern)" 为选择器，表示匹配 pattern 并获取这一匹配的子字符串。
-----------------------------

## Example 2 -- 获取邮件头文件中的发件人地址的域
Patten:

    "From: .*@(.*)"

Output:

    ['uct.ac.za', 'uct.ac.za']

Explanation

    "From: .*@(.*)"
    "From: " 即匹配原文中的 "From: "，
    "." 匹配任意字符，除 '\n' 外，
    "*" 匹配前面的子表达式零次或多次，在此处为匹配 "." 即任意字符零次或多次，
    "@" 即匹配原文中的 "@"
    "(pattern)" 为选择器，表示匹配 pattern 并获取这一匹配的子字符串。
-----------------------------

## Example 3 -- 获取邮件头文件中的发件人地址的域为media.berkeley.edu或uct.ac.za的地址

Patten:

    "From: (.*@(?:media.berkeley.edu|uct.ac.za))"

Output:

    ['stephen.marquard@uct.ac.za', 'louis@media.berkeley.edu']

Explanation

    "From: (.*@(?:media.berkeley.edu|uct.ac.za))"
    "From: " 即匹配原文中的 "From: "，
    "." 匹配任意字符，除 '\n' 外，
    "*" 匹配前面的子表达式零次或多次，在此处为匹配 "." 即任意字符零次或多次，
    "@" 即匹配原文中的 "@"
    "(?:pattern)" 匹配 pattern 但不获取匹配的子字符串
    "media.berkeley.edu|uct.ac.za" 匹配 "media.berkeley.edu" 或 "uct.ac.za"
    "(pattern)" 为选择器，表示匹配 pattern 并获取这一匹配的子字符串。