This is a transcript for the video: "Panda Lecture from Oct 8, 2003: Characters, part 1"  
Original video URL: https://www.youtube.com/watch?v=sePa3e7-lZQ  
Speech disfluencies (um, uh) have been removed  
Lecturer: David Rose  
Assume lecturer is speaking unless indicated otherwise  

-Start of video-

So let's see, any objections to talking about characters? We use them every day, I think (Unintelligible) is particularly good at them.

Most of the time we don't have to think much about what goes on inside. The first question that comes to mind is 'What is a character?' and I had a hard time figuring it out last time.
 
I thought about it a little bit more, I guess in the panda sense a character is any model/animated character converted from an animation package such as SoftImage or Maya or Alias.  
Typically a single scene in that package, which usually corresponds to a character but might be a prop or some single model.

There are exceptions:  
In the case of the Toons[1] there are actually three characters each because we had to have the split body Toons to be able to switch in and out heads, and feet, and torsos and stuff like that.

But we only did that because we had to, if we had a (Unintelligible) make the character Toons would be just one big character.

At the first level a character starts off in some package, in Maya for instance, and it consists of a skeleton and a series of polygons or whatever the animators created is attached to the skeletons.

So the modeller is reponsible for creating the character, create dimension polygons, and associating each polygon with one or more joints, so that as he animates a character the polygons move with the joints.

Typically there's either hard skinning or soft skinning. In hard skinning the polygon pocket is parented directly to the joint, which is pretty much what we used to do with the scene graph.  

In soft skinning, a polygon could actually shares vertices between different joints. There might be some vertices in this joint and some vertices in another joint. Furthermore, each vertex might not be entirely one joint or another, some individual vertices might be partially one joint partially another joint. That's how you get the nice smooth effects of elbows and stuff like that.  

Audience Member: And then you can tweak how much they're influenced by each of them separately.  

Yes, and nowadays all these animation packages have nice tools where you can relatively easily set up the skinning ratio, you just say basically here's my polygons here's the skeleton click, boom, it's all done. So I'm told.  

So at some point we run Maya2Egg, or Soft2Egg, or Max2Egg or whatever the heck we're running, and we produce an .egg file.  
Typically at least two .egg files for each character, because we have one for the model, and then we might have a different .egg file for each animation, say for instance a swimming animation.  

Now the model file and the animation file are totally different kinds of files. The model file has just polygons and joints, which reflects [the skeleton and mesh] hierarchy, and the animation file just has a table of frames, matrix positions, one per joint per frames.  

They don't have to be different .egg files, its possible for these to be the same .egg file, but typically we make them separate .egg files because we have multiple animations, we want to be able to mix and match particular animations we want to play.  

A lot of times if we have the same skeleton which can play multiple animations in one go.  

The representation in .egg is worth talking about on its own, it's somewhat different from the representation within Panda. Once we load it in Panda, it gets converted into a different form altogether. I'll come back to the .egg representation.  

Once we load it into Panda, we have a character node ultimately, at the top of the scene graph. If we just look at it, he's probably just got one child, which is a Geom node once we load it up.  

It doesn't look very much on the outside in the scene graph. Sometimes, depending on what flags we have in the .egg file, he might have multiple Geom nodes. Typically, there's a character and probably just one Geom node.  

We actually have some controls on the character, once you get to the character node, we can then load up the animation, so this would be the model for instance, toon0.egg. Now it's just toon0, we just loaded the egg file and have this character node.  

If we load the anim file, we get an AnimBundleNode, this would be toon swim. So we can take the AnimBundle, which is just a single node, but inside this AnimBundle node is stored all the animation data that we loaded from the swim animation, and we can call the character mechanism to bind the animation to the character and start to play it, then the character seems to start swimming. So the Geom node, the vertices are actually changing.


-Notes-  
[1]. "Toons" refers to the customizable player avatars from the Panda3D game "Toontown Online"