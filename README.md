TODO:
- explain the motivation behind `tiny_actor`
- compare/contrast it to `Ractor`
- move all of this explanation into `lib/tiny_actor.rb` like the other tiny gems

```ruby
# thinking that the syntax here should be something like what's below, and start
# with a simple spawning capability
#
# https://stackoverflow.com/questions/46121918/how-to-hello-world-programmatically-on-remote-machine-in-elixir

# assuming you're running TinyActor on two computers:
# - localhost
# - 192.168.0.29

# this will create:
# - a new process on the remote host at 192.168.0.29
# - named 'worker'
# - runnin a service named 'image_resizer'
img_resizer_local = TinyActor.spawn('worker@localhost/img_resizer')
img_resizer_remote = TinyActor.spawn('worker@192.168.0.29/img_resizer')

img_resizer_local.send('https://test.com/img-12345.png 200x200 400x400 600x600')
img_resizer_remote.send('https://test.com/img-54321.png 200x200 400x400 600x600')

# some notes:
# if you want to spawn on the local machine you can specify `localhost`, since
# using TinyActor should open up a local spawner
#
# do I really need named remote processes? maybe helpful for debugging, but the
# local variabl name is the thing that gives them a name locally.
```
