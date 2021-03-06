# Groovy Client DSL

This project provides a DSL inspired in Gradle and Jenkins Pipelines to write Conductor clients.

Here's a sample worker:

```groovy
@GrabResolver(name='orkes-repo', root='https://orkes-artifacts-repo.s3.amazonaws.com/releases', m2Compatible='true')
@Grab("io.orkes.conductor:groovy-dsl-client:0.2.0")
import static io.orkes.client.dsl.Worker.worker
import com.netflix.conductor.common.metadata.tasks.TaskResult

worker {
    rootUri 'https://play.orkes.io/api/'
    name 'hello_world_worker'
    keyId '_CHANGE_ME_' // Create an Application and Access Key on Conductor UI
    secret '_CHANGE_ME_'
    start {
        println('Hello World!')
        TaskResult.complete()
    }
}
```

To run this worker (assuming you have Groovy 3.0.x installed) you can execute:

```bash
groovy hello-world-worker.groovy
```
