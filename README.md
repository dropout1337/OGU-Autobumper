Firstly [OGU](https://ogu.gg/) has cloudflare, so to access ogu using requests we can't use the standard requests library.
In this case I'm using [tls_client](https://github.com/FlorianREGAZ/Python-Tls-Client).

Make sure you set the `ogumybbuser` cookie in all the requests.

#

Okay, now when replying to a post you need the following parameters:<br>
`my_post_key`, `subject`, `action`, `posthash`, `quoted_ids`, `lastpid`, `from_page`, `tid`, `method`, `message`, `postoptions[signature]`

#

To get most of these we can send a GET request to your thread url. Then we can get the following parameters:<br>
`my_post_key` (`"my_post_key" value="(.*)"`), `subject` (`"subject" value="(.*)"`), `posthash` (`"posthash" value="(.*)" id="posthash"`), `lastpid` (`"lastpid" value="(.*)"`), `tid` (`"tid" value="(.*)"`)

#

Now just post to `https://ogu.gg/newreply.php?ajax=1` with the form-urlencoded data:<br>
my_post_key={mypostkey}<br>
subject={subject}<br>
action=do_newreply<br>
posthash={posthash}<br>
quoted_ids=<br>
lastpid={lastpid}<br>
from_page=1<br>
tid={tid}<br>
method=quickreply<br>
message={replymessage}<br>
postoptions[signature]=1<br>

#

I know, shit explination but deal with it.
