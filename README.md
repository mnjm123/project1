# file-optimization
</head>
<body>

  <h2>Problem</h2>
  <p>
    On macOS, everything I download from the Internet will land on the Downloads folder.
  </p>
  <p>
    After a while, this folder becomes a mess of all file types that I may or may not need.
    It's a pain point for me as I use my laptop for all things school, work and personal needs related.
  </p>

  <h2>Solution requirements</h2>
  <p>With the above pain point, I need a solution to:</p>
  <ol>
    <li>Cleanup my Downloads folder periodically (ideally every day) so whenever there is a newly downloaded file, I can spot them right away.</li>
    <li>Keep an archive of all the old files, well, just in case.</li>
  </ol>

  <h2>Introducing: File Organizer (FO)</h2>
  <p><em>(Excuse my poor naming attempt, this app is not for commercial distribution yet!)</em></p>

  <h3>What does it do?</h3>
  <ul>
    <li>(With minimal setup) FO will run periodically (set by you) to bring all the files of the same type into the same folder.</li>
  </ul>

</body>
</html>
<h2>How to use FO?</h2>
<ol>
  <li>See that lil green button with '&lt;&gt; Code' word up there? Yes, on the upper right. Click on it. Download the ZIP.</li>
  <li>If you're pro and want to prove your un-laziness to no one, go ahead and run the main.py in the ZIP. Otherwise, skip this step.</li>
  <li>Go to <code>dist/main</code>, and click on the file 'main'. Yes that lil black one that looks like the terminal window.</li>
  <li>The program will run, opening a window for you to select the folder you want to clean up.</li>
  <li>Choose the folder and let the magic work. Check your folder and gasp in disbelief.</li>
</ol>

<p><em>Eh wait, didn't you promise that this program will run periodically?</em></p>

<p>Yes! It's possible, with some tweaks. To make that happen, we need the help of Crontab 👇</p>

<h2>How to use Crontab to automate your program?</h2>
<p>On macOS, there's a program called <strong>Crontab</strong> that can let you schedule a task to run periodically. Follow these steps to set up Crontab to work with FO:</p>

<ol>
  <li>Open your terminal, type <code>crontab -e</code> to open the editor of crontab</li>
  <li>Press <code>i</code> to enter "insert" mode (equivalent: edit mode, stupid name)</li>
</ol>
<ol start="3">
  <li>
    Use the special command of crontab to schedule.
    <p>After rigorous search attempt, I figured out the <strong>correct</strong> command to use for my computer (why doesn’t the Internet have it before?). It's in this format:</p>
    <pre><code>[special_command_for_the_schedule] [space] [path_to_the_executable_file_dont_input_the_extension]</code></pre>
    <p><strong>Example:</strong> I want to run the program everyday at 10AM</p>
    <pre><code>0 10 * * * /Users/{your_username}/Downloads/python-file-organizer/file-organizer/dist/main/main</code></pre>
    <p><em>Notes: For the special commands of crontab, visit: 
      <a href="https://crontab.guru/" target="_blank">https://crontab.guru/</a></em>
    </p>
  </li>
  <li>
    After you write the command, press <kbd>Esc</kbd> to exit the "insert" mode. Then type <kbd>:wq</kbd> (<strong>w</strong> - write, <strong>q</strong> - quit), press <kbd>Enter</kbd> to run the command.
  </li>
  <li>
    If the command is run successfully, you'll see a system popup of crontab asking for permission to administer your computer. Allow it.
  </li>
  <li>
    To double check that the crontab is created, you can write <code>crontab -l</code>.
  </li>
  <li>
    If you want to delete the job you just created, write <code>crontab -r</code>.
  </li>
  <li>
    That's it! Now our program will run on the period that we've just specified.
  </li>
</ol>
