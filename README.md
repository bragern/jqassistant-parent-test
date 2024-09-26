### "mvn clean install" on parent:

> ...
> 
> [INFO] --- jqassistant-maven-plugin:2.4.0:analyze (default-cli) @ jqassistant-test-child ---
> 
> [INFO] Loading YAML configuration from 'jar:file:/C:/Users/user/.m2/repository/com/buschmais/jqassistant/jqa-distribution-specification/2.4.0/jqa-distribution-specification-2.4.0.jar!/.jqassistant.yml' (priority: 80).
> 
> [INFO] Loading YAML configuration from 'file:/C:/jqassistant-test/jqassistant-test-child/.jqassistant.yml' (priority: 150).
> 
> [INFO] Rules directory **'C:\jqassistant-test\jqassistant'** does not exist, skipping.
> 
> ...
> 
> <span style="color:red">**[ERROR] Failed to execute goal com.buschmais.jqassistant:jqassistant-maven-plugin:2.4.0:analyze (default-cli) on project jqassistant-test-child: Analysis failed.: Cannot find group my-concepts -> [Help 1]**</span>
> 
> ...
> 
> <span style="color:red">**[INFO] BUILD FAILURE**</span>

This searches for the rules directory within parent - unexpected behavior. ❌

### "mvn clean install" on child:

> ...
> 
> [INFO] --- jqassistant-maven-plugin:2.4.0:analyze (default-cli) @ jqassistant-test-child ---
> 
> [INFO] Loading YAML configuration from 'file:/C:/jqassistant-test/jqassistant-test-child/.jqassistant.yml' (priority: 100).
> 
> [INFO] Loading YAML configuration from 'jar:file:/C:/Users/user/.m2/repository/com/buschmais/jqassistant/jqa-distribution-specification/2.4.0/jqa-distribution-specification-2.4.0.jar!/.jqassistant.yml' (priority: 80).
> 
> [INFO] Reading rules from directory **'C:\jqassistant-test\jqassistant-test-child\jqassistant'**.
> 
> [INFO] Executing analysis for 'jqassistant-test-child'.
> 
> [INFO] Executing group 'my-concepts'
> 
> ...
> 
> <span style="color:green">**[INFO] BUILD SUCCESS**</span>

This searches for the rules directory within child - expected behavior. ✅