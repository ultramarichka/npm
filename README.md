1. npm help ............ Get help with npm  

3. However, when you run  
     this in the Real World, it'll create a real account, with a page  
     on npmjs.com and the ability to publish packages that real live  
     humans can install and enjoy.  
       
     To see who you're logged in as, run `npm whoami`  
       
     To create your account, run `npm adduser`  

4. Run `npm init --scope=<username>`, and replace <username> with the user  
     you created in the last lesson. This will create a package.json file.  
     (For extra credit, set the project up with a git repo as well.)  

5. The first thing that most people do with npm is install a dependency.  
       
     Dependencies are fetched from the registry, and unpacked in the    `node_modules`  
     folder.  
       
     To install a module, use the `npm install <modulename>` command.  

     Let's start out by installing the "@linclark/pkg" module.  

6. `npm ls`
7. "scripts": {  
         "test": "node test.js"  
       },

8. If you type `npm install`, you'll see  
     something like this:  
       
         npm WARN package.json %ID% No description  
         npm WARN package.json %ID% No repository field.  
         npm WARN package.json %ID% No README data  
       
     Before we can share this work of art with the world, we need to make  
     it a bit more polished so that people know how to use it.  
       
     First, create a README.md file, with a few words in it.  
       
     Then, add a "repository" field in your package.json file, with a url  
     where people can access the code.  
       

9.`npm publish`
10. Every package in npm has a version number associated with it.  As  
     you release updates to your package, these updates get an updated  
     version number.  
       
     Version numbers in npm follow a standard called "SemVer".  This stands  
     for "Semantic Version".  The specification for this standard can be  
     found at http://semver.org.  
       
     The tl;dr version is that for a version like this:  
       
       1.2.3  
       ^ ^ ^  
       | | `-- Patch version. Update for every change.  
       | `---- Minor version. Update for API additions.  
       `------ Major version. Update for breaking API changes.  
       
     npm has a special command called `npm version` which will update your  
     package.json file for you, and also commit the change to git if your  
     project is a git repository.  You can learn more at `npm help version`.  
       
     Or, if you don't trust the machines, you can open up your package.json  
     file by hand, and put some new numbers in the "version" field.  
       
     The npm registry won't let you publish a new release of your package  
     without updating the version number!  Ever!  So, get used to the idea of  
     bumping the version whenever you want to publish, even if the change is  
     really minor.  
       
     Don't worry, there's a lot of integers, we probably won't run out.  
     You can edit your package.json file by hand, or run `npm init` again.  

11. DIST TAG 
    Every published package on npm has a `dist-tags` entry on it which  
     maps strings like "latest" to version numbers like "1.2.48".  
       
     By default, the "latest" version is what gets installed.  When you  
     publish, the version that you publish gets tagged as "latest".

     However, if you need to publish something, and *not* make it the  
     default version of a package (for example, if it's a security release  
     for a legacy version, or something), then you can manually manage  
     these distribution tags with the `dist-tag` function.  
       
     `npm dist-tag add <pkg>@<version> [<tag>]` will add a new tag.  
     To find out the name of your current package/version type `npm ls`.  
     The first line of the output will be the package and version; e.g. pkg@1.0.1.  
     To add a tag type in the name of the tag.  
       
       npm dist-tag add pkg@1.0.1 beta  
       
12. REMOVE DIST-TAG 
    The only dist-tag you CAN'T ever remove is "latest".  That's because  
     every package installs its "latest" tag by default, so that tag has  
     some special semantics.  
       
     You CAN point "latest" to a different version, or delete other tags.  
       
     Let's delete all the tags that we can, and also point "latest" at  
     something other than the most recent release.  
       
     Run `npm help dist-tag` to learn more about the command.

14. UPDATE all of your deps to the max version you allow in your package.json.  
     (`npm help` might help you) 

15. DELETE dependencies
    Enter the `npm rm` command (aka `npm uninstall` if you prefer to  
     type things out long-hand).  
       
     Remove all the deps!  But, make sure that you don't keep depending on them.  
       
     Just like you can use `--save` on installing packages, you can also  
     use `--save` when removing packages, to also remove them from your  
     package.json file.  
