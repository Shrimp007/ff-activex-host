# Introduction #
To have more than one ffactivex instance (for easier
maintenance, less dependencies, easier uninstall), you can use use separate
Mime Types. This also prevents other ffactivex users on the same
from interfering with your installation (and vice versa).

Because the plugin API requires the supported MimeTypes in the version
resource of the plugin and you might not want to add a
dependency to the complete Mozilla source and ffactivex to your
projects, there is a small tool, which transplants a version
resource from one executable (which only includes the required version
resource) to another (npffax.dll).

# Details #

```
TRANSVER <source> <target>
```

| Parameter | Description |
|:----------|:------------|
| 

&lt;source&gt;

 | Source file with version resource |
| 

&lt;target&gt;

 | File for version resource |

## Sample Usage ##
```
TRANSVER ffaxver.dll npffax.dll
```