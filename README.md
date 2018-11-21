---


---

<h1 id="java_term_project">JAVA_Term_Project</h1>
<p>JAVA Term project(Simple Music Player)<br>
<img src="https://user-images.githubusercontent.com/44791701/48841342-7feeb480-edd4-11e8-81a5-baf1ca53bd55.JPG" alt="1"></p>
<h2 id="explanation">Explanation</h2>
<p>Worked together to create a simple music player</p>
<h2 id="main.java">Main.java</h2>
<p>A java file that calls MusicPlayer.java</p>
<ul>
<li>
<p>The program run in the corresponding Java file</p>
<pre><code> public  static  void  main(String[] args) {
     MusicPlayer  mp  =  new  MusicPlayer();
 } // Call MusicPlayer.java
</code></pre>
</li>
</ul>
<h2 id="musicplayer.java">MusicPlayer.java</h2>
<p>Here is the code for the player to run.</p>
<p><img src="https://user-images.githubusercontent.com/44791701/48841342-7feeb480-edd4-11e8-81a5-baf1ca53bd55.JPG" alt="1"></p>
<pre><code>MusicPlayer()
{
    this.setBackground(Color.WHITE);
    window.add(this);
    addButton.setSize(500,500);
    playButton.setSize(500,500);
    stopButton.setSize(120,120);
    addButton.addActionListener(this);
    playButton.addActionListener(this);
    stopButton.addActionListener(this); //Make a listener
    
    JPanel  panel;
    panel =  new  JPanel();
    panel.setLayout(new  FlowLayout(FlowLayout.CENTER));
    info.setFont(new  Font("",Font.ITALIC,12));
	    window.add(info,BorderLayout.PAGE_END);
    panel.add(playButton);
    panel.add(stopButton);
    panel.add(addButton); // Declare Buttons 
    add(panel);
    window.add(list,BorderLayout.PAGE_START);
    browser.setFileFilter(filter);

    window.setSize(400,200);
    window.setLocation(100, 100); //Set window size at runtime
    window.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    window.setVisible(true);
} // Functions that make up the UI
</code></pre>
<ul>
<li>Action Part</li>
</ul>
<ol>
<li>
<p>Add file<br>
<img src="https://user-images.githubusercontent.com/44791701/48841387-a3196400-edd4-11e8-94e1-122bc32ccab5.JPG" alt="addmusic"></p>
<pre><code> if(ae.getSource()==addButton) // press addbutton
 	{
 		returnValue =  browser.showOpenDialog(window); //Call search window
 		if(returnValue ==  browser.APPROVE_OPTION)
 			{
 				selectedFile =  browser.getSelectedFile();
 				musics[index] =  selectedFile.toString();
 				list.addItem("Song - "  + index+"-"+musics[index]);
 				index++; // Count index number
 			}// Add .wav files after search
 	}
</code></pre>
</li>
<li>
<p>Play .wav files<br>
<img src="https://user-images.githubusercontent.com/44791701/48841424-be846f00-edd4-11e8-8557-f20805a978ea.jpg" alt="list"></p>
<pre><code> else  if(ae.getSource()==playButton) //press paybutton
 	{
 		try{
 				for(int  a=0; a&lt;100; a++){
 					if(list.getSelectedIndex()==a)
 					{
 						sound =  new  File(musics[list.getSelectedIndex()]);
 						ais =  AudioSystem.getAudioInputStream(sound);
 						clip =  AudioSystem.getClip();
 						clip.open(ais); //open .wav file
 						clip.start(); // play the file
 					}
 					else  if(list.getSelectedIndex()==a+1)
 					{
 						clip.stop(); // The next song will stop once it is played
 					}
 			}
 	}
 	catch(Exception  e){JOptionPane.showMessageDialog(null, e);} // Code to isolate errors
 }
</code></pre>
</li>
<li>
<p>Stop Button</p>
<pre><code> else  if(ae.getSource()==stopButton)
 	{
 		clip.stop();
 	}
</code></pre>
</li>
</ol>
<h2 id="caution">Caution</h2>
<ul>
<li>MusicPlayer can play .wav file ONLY.</li>
</ul>

