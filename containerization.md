---


---

<h1 id="containerization">Containerization</h1>
<ul>
<li>
<p><strong>Virtualization and Hypervisors</strong></p>
<ul>
<li><strong>Virtualization:</strong> Allows one physical machine to run multiple isolated <strong>Virtual Machines (VMs)</strong>, each with its own OS, kernel, applications, and virtual hardware.</li>
<li><strong>Hypervisor:</strong> Software that creates and manages VMs by allocating resources such as CPU, RAM, storage, and networking.</li>
<li><strong>Type 1 Hypervisor:</strong> Runs directly on the physical hardware and manages VMs.
<ul>
<li><code>Hardware → Type 1 Hypervisor → VMs</code></li>
<li>Common in servers and data centres.</li>
<li>Examples: VMware ESXi, Microsoft Hyper-V Server.</li>
</ul>
</li>
<li><strong>Type 2 Hypervisor:</strong> Runs as an application on a normal host OS.
<ul>
<li><code>Hardware → Host OS → Type 2 Hypervisor → VMs</code></li>
<li>Example: VirtualBox running on Linux.</li>
</ul>
</li>
<li><strong>Key difference:</strong> A VM includes its own <strong>OS kernel</strong>, while containers normally share the host OS kernel.</li>
</ul>
</li>
<li>
<p><strong>Containers and Docker</strong></p>
<ul>
<li><strong>Container:</strong> An isolated environment for running an application and its dependencies while sharing the host OS kernel.</li>
<li>Unlike VMs, containers don’t have their own kernel, making them <strong>lighter, faster to start, and more resource-efficient</strong>.</li>
<li>A container can still have an OS userspace such as Ubuntu or Alpine, including its libraries and utilities, but the <strong>kernel comes from the host</strong>.</li>
<li>This is why an Ubuntu-based container can run on Fedora, Arch, Debian, etc., as long as a compatible Linux kernel/container runtime is available.</li>
<li><strong>Namespaces:</strong> Isolate what a container can see, such as processes, users, networking, and filesystems.</li>
<li><strong>cgroups:</strong> Control and limit resources available to containers, such as CPU and memory.</li>
<li><strong>Microservices:</strong> Applications can be split into smaller independent services, with each service running in its own container.</li>
<li><strong>Docker:</strong> A platform used to build, package, run, and manage containers.
<ul>
<li><strong>Image:</strong> Read-only template used to create containers.</li>
<li><strong>Container:</strong> Running instance of an image.</li>
<li><strong>Dockerfile:</strong> Instructions used to build an image.</li>
<li><strong>Base image:</strong> Provides the userspace/filesystem for a container, e.g. <code>ubuntu</code> or <code>alpine</code>; it does <strong>not</strong> provide its own kernel.</li>
</ul>
</li>
<li>Example:<pre class=" language-bash"><code class="prism  language-bash">docker run -p 8000:5000 -d myapp
</code></pre>
<ul>
<li><code>-d</code> → runs the container in the background (detached mode).</li>
<li><code>-p 8000:5000</code> → maps <strong>host port 8000 → container port 5000</strong>.</li>
<li>“What port do I want outside?” : “What port is the app listening on inside?”</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Kubernetes</strong></p>
<ul>
<li>
<p><strong>Kubernetes (K8s):</strong> A container orchestration platform used to deploy, manage, scale, and maintain containers across one or more machines.</p>
</li>
<li>
<p>Instead of manually managing many containers, Kubernetes maintains a <strong>desired state</strong>. For example, if we request 3 replicas and one fails, Kubernetes creates another to return to 3.</p>
</li>
<li>
<p><strong>Cluster</strong></p>
<ul>
<li>The complete Kubernetes environment containing the machines and resources managed by Kubernetes.</li>
<li><code>Cluster → Nodes → Pods → Containers</code></li>
</ul>
</li>
<li>
<p><strong>Node</strong></p>
<ul>
<li>A physical or virtual machine that runs Kubernetes workloads.</li>
<li>A cluster can contain multiple nodes.</li>
</ul>
</li>
<li>
<p><strong>Pod</strong></p>
<ul>
<li>The <strong>smallest deployable unit in Kubernetes</strong>.</li>
<li>A Pod contains <strong>one or more containers</strong> that share networking and can share storage.</li>
<li>Most commonly:<pre class=" language-text"><code class="prism  language-text">Pod
└── Container
    └── Application
</code></pre>
</li>
<li>Multiple containers can exist in one Pod when they are tightly coupled and need to work together, e.g. a main application container and a logging/proxy <strong>sidecar</strong>.</li>
<li>Containers inside the same Pod share the Pod’s network namespace and can communicate using <code>localhost</code>.</li>
<li>Pods are temporary/disposable; Kubernetes can create replacement Pods when they fail.</li>
<li><strong>Important:</strong> Kubernetes manages Pods rather than individual containers.</li>
</ul>
</li>
<li>
<p><strong>ReplicaSet</strong></p>
<ul>
<li>Ensures that a specified number of identical Pods are running.</li>
<li>Example:<pre class=" language-text"><code class="prism  language-text">ReplicaSet
├── Pod 1
├── Pod 2
└── Pod 3
</code></pre>
</li>
<li>If one Pod fails, the ReplicaSet creates another to maintain the desired number of replicas.</li>
</ul>
</li>
<li>
<p><strong>Deployment</strong></p>
<ul>
<li>Manages ReplicaSets and provides higher-level management of applications, including <strong>scaling and rolling updates</strong>.</li>
<li>Main management relationship:<pre class=" language-text"><code class="prism  language-text">Deployment
    ↓
ReplicaSet
    ↓
  Pods
    ↓
Containers
    ↓
Application
</code></pre>
</li>
</ul>
</li>
<li>
<p><strong>Service</strong></p>
<ul>
<li>Provides a <strong>stable network endpoint</strong> for accessing a group of Pods.</li>
<li>Pods are temporary and their IP addresses can change, so clients should communicate with a Service instead.</li>
<li>A Service selects appropriate Pods and forwards traffic to them.</li>
<li><strong>The Service is a networking object, not part of the Deployment → Pod hierarchy.</strong></li>
<li>Networking relationship:<pre class=" language-text"><code class="prism  language-text">Client
   ↓
Service
   ↓
┌──────┼──────┐
↓      ↓      ↓
Pod    Pod    Pod
</code></pre>
</li>
<li>The Service does <strong>not</strong> select individual containers; it selects Pods. The application being accessed is running inside a container within the selected Pod.</li>
<li>Example:<pre class=" language-yaml"><code class="prism  language-yaml"><span class="token key atrule">ports</span><span class="token punctuation">:</span>
  <span class="token punctuation">-</span> <span class="token key atrule">port</span><span class="token punctuation">:</span> <span class="token number">80</span>
    <span class="token key atrule">targetPort</span><span class="token punctuation">:</span> <span class="token number">8080</span>
</code></pre>
<ul>
<li><code>port</code> → port exposed by the Service.</li>
<li><code>targetPort</code> → port where the application is listening inside the Pod.</li>
</ul>
</li>
</ul>
</li>
<li>
<p><strong>Namespace</strong></p>
<ul>
<li>Logically separates resources within a Kubernetes cluster.</li>
<li><code>default</code> → commonly contains user/application resources.</li>
<li><code>kube-system</code> → contains Kubernetes system components such as CoreDNS and other system Pods.</li>
<li>Example:<pre class=" language-bash"><code class="prism  language-bash">kubectl get pods -n kube-system
</code></pre>
</li>
</ul>
</li>
<li>
<p><strong>Minikube</strong></p>
<ul>
<li>Creates a small Kubernetes cluster locally for learning, development, and testing.</li>
<li>Start a cluster:<pre class=" language-bash"><code class="prism  language-bash">minikube start
</code></pre>
</li>
</ul>
</li>
<li>
<p><strong>kubectl</strong></p>
<ul>
<li>Command-line tool used to interact with and manage a Kubernetes cluster.</li>
<li>Common commands:<pre class=" language-bash"><code class="prism  language-bash">kubectl get pods
kubectl get deployments
kubectl get replicasets
kubectl get services
kubectl get all
</code></pre>
</li>
<li>View system Pods:<pre class=" language-bash"><code class="prism  language-bash">kubectl get pods -n kube-system
</code></pre>
</li>
<li>Get detailed information:<pre class=" language-bash"><code class="prism  language-bash">kubectl describe pod <span class="token operator">&lt;</span>pod-name<span class="token operator">&gt;</span>
kubectl describe deployment <span class="token operator">&lt;</span>deployment-name<span class="token operator">&gt;</span>
kubectl describe <span class="token function">service</span> <span class="token operator">&lt;</span>service-name<span class="token operator">&gt;</span>
</code></pre>
</li>
<li>Delete a Deployment:<pre class=" language-bash"><code class="prism  language-bash">kubectl delete deployment <span class="token operator">&lt;</span>deployment-name<span class="token operator">&gt;</span>
</code></pre>
</li>
</ul>
</li>
<li>
<p><strong>Kubernetes Big Picture</strong></p>
<ul>
<li><strong>Management/lifecycle:</strong><pre class=" language-text"><code class="prism  language-text">Deployment
    ↓
ReplicaSet
    ↓
┌──────┼──────┐
↓      ↓      ↓
Pod    Pod    Pod
│      │      │
Container Container Container
│      │      │
App    App    App
</code></pre>
</li>
<li><strong>Networking:</strong><pre class=" language-text"><code class="prism  language-text">Client
   ↓
Service
   ↓
┌──────┼──────┐
↓      ↓      ↓
Pod    Pod    Pod
</code></pre>
</li>
<li><strong>Key relationships:</strong>
<ul>
<li><code>Deployment → manages ReplicaSets</code></li>
<li><code>ReplicaSet → maintains Pods</code></li>
<li><code>Pod → contains one or more Containers</code></li>
<li><code>Container → runs the Application</code></li>
<li><code>Service → Provides a stable network endpoint for clients to access a group of Pods, even when individual Pod IP addresses change.</code></li>
<li><code>Cluster → contains Nodes</code></li>
</ul>
</li>
</ul>
</li>
</ul>
</li>
</ul>

