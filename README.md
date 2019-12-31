# ActiveMQ-Installation
Guide to Install Apache ActiveMQ on Windows &amp; Unix

<p><a href="http://activemq.apache.org/" target="_blank">Apache ActiveMQ</a> is an <strong>open source message broker</strong> written in Java that offers JMS, REST and WebSocket interfaces. It supports protocols like AMQP, MQTT, OpenWire, and STOMP that can be used by applications in different languages.</p>

<p>Following tutorial details how to install ActiveMQ on Windows or Unix and in addition shows how to perform a start/stop of the installed instance.</p>

<p>First thing to do is to download the ActiveMQ binaries. Go the the <a href="http://activemq.apache.org/download.html" target="_blank">ActiveMQ download page</a> and click on the latest stable release link in the <var>Latest Releases</var> section. Then in the <var>Getting the Binary Distributions</var> section click on the download link for your operating system. At the time of writing the latest stable release was <var>apache-activemq-5.13.3</var>.</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/apache-activemq-download.png" alt="apache activemq download" />
</figure>

<h1 id="install-activemq-on-windows">Install ActiveMQ on Windows</h1>

<p>Extract the Windows binaries archive that was downloaded in the previous step. The extracted root directory should contain a number of files and subdirectories as shown below. From now on we will refer to this directory as: <var>[activemq_win_install_dir]</var>.</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/windows-apache-activemq-files.png" alt="windows apache activemq files" />
</figure>

<p>Open a command prompt and navigate to <var>[activemq_win_install_dir]</var>. Change to the <var>bin</var> subdirectory and execute the following command to start ActiveMQ:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>activemq start
</code></pre></div></div>

<p>By default ActiveMQ will generate a number of log statements at start-up as shown below:</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/windows-apache-activemq-startup-trace.png" alt="windows apache activemq startup trace" />
</figure>

<p>One of the latest log entries will mention <var>'ActiveMQ WebConsole available at http://0.0.0.0:8161/'</var>. This indicates that ActiveMQ was successfully started.</p>

<h1 id="install-activemq-on-unix">Install ActiveMQ on Unix</h1>

<p>Extract the Unix binaries archive downloaded in the first step. The extracted root directory should contain a number of files and subdirectories as shown below. From now on we will refer to this directory as: <var>[activemq_unix_install_dir]</var>.</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/unix-apache-activemq-files.png" alt="unix apache activemq files" />
</figure>

<p>Open a terminal and navigate to <var>[activemq_unix_install_dir]</var>. Change to the <var>bin</var> subdirectory and execute the following command to start ActiveMQ as a foreground process:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>./activemq console
</code></pre></div></div>

<p>The ActiveMQ broker can also be started as a background process (note that the corresponding process identifier is stored in the <var>[activemq_unix_install_dir]/data</var> directory for future reference). In order to achieve this, execute the following command instead of the above (hit <var>CTRL+C</var> first if you already started using a foreground process).</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>./activemq start
</code></pre></div></div>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/unix-apache-activemq-start.png" alt="unix apache activemq start" />
</figure>

<p>Once started as a background process there are a number of additional commands we can run to manage the running broker instance. For example, execute the following to see if ActiveMQ is still running:</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>./activemq status
</code></pre></div></div>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/unix-apache-activemq-status.png" alt="unix apache activemq status" />
</figure>

<p>The ActiveMQ web site contains a <a href="http://activemq.apache.org/unix-shell-script.html#UnixShellScript-Functionaloverview" target="_blank">complete overview of the available Unix commands</a>. In order to stop the background process, use the below command, but for now, leave the broker running as we will first explore the web console.</p>

<div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>./activemq stop
</code></pre></div></div>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/unix-apache-activemq-stop.png" alt="unix apache activemq stop" />
</figure>

<p>Note that if you would like ActiveMQ to start automatically at system startup you would need to <a href="http://activemq.apache.org/unix-shell-script.html#UnixShellScript-Runningactivemqasaunixdaemon" target="_blank">run the ActiveMQ broker as a Unix daemon process</a>.</p>

<h1 id="activemq-webconsole">ActiveMQ WebConsole</h1>

<p>The ActiveMQ Web Console is a web-based administration tool for working with ActiveMQ. The console can be accessed by entering the following URL in a web browser: <a href="http://localhost:8161/">http://localhost:8161/</a>. If ActiveMQ is up and running and installed successfully, following welcome page should be displayed:</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/apache-activemq-console.png" alt="apache activemq console" />
</figure>

<p>Click on the <var>Manage ActiveMQ broker</var> link and enter following default credentials: User name=”<kbd>admin</kbd>” and Password=”<kbd>admin</kbd>”. A home page will be displayed that shows some basic statistics on the ActiveMQ broker. In addition it contains a number of menus that allow you to explore the different configuration items (queues, topics, connections, …) of the broker.</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/apache-activemq-console-welcome.png" alt="apache activemq console welcome" />
</figure>

<p>Let’s finish this tutorial by stopping the running ActiveMQ instance. Switch back to the console in which ActiveMQ was started and press <var>CTRL+C</var> (note that if ActiveMQ was started as a background process, the stop command needs to be run instead). If needed type “<kbd>Y</kbd>” when prompted to <var>'Terminate batch job'</var> followed by <var>ENTER</var>. The console will return to the prompt as shown below and ActiveMQ is stopped.</p>

<figure>
    <img src="https://github.com/ShahbazHaroon/ActiveMQ-Installation/blob/master/img/apache-activemq-stop.png" alt="apache activemq stop" />
</figure>

<p>This concludes setting up and configuring Apache ActiveMQ.</p>
