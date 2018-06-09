<div class="single_post"> <header><h1 class="title single-title entry-title" itemprop="headline">Android Material Design Navigation Drawer With Header View</h1> </header><!--.headline_area--><div class="post-single-content box mark-links entry-content"><div class="thecontent" itemprop="articleBody"><h3>Android Material Design Navigation Drawer With Header View</h3><p>In this tutorial we are going to learn how to implement android Navigation Drawer with Header View. Some&nbsp;recent android applications have used the Header View in Navigation Drawer like in GMail android application.</p><p>I wrote an extensive tutorial on <i><b><a href="https://inducesmile.com/android/android-navigation-drawer-with-material-design/" target="_blank">Android Navigation Drawer with Material Design</a></b></i>.<i><b> </b></i>I will suggest you read the post first because we will focus on the slight difference between the two application projects. <i><b> </b></i></p><p>What we have achieved in the first tutorial is to create a Navigation Drawer with a ListView and an event listener is attached to the navigation items. The final result is as shown below.</p><p><a href="https://inducesmile.com/wp-content/uploads/2015/05/navieight.jpg"><img class="alignnone size-full wp-image-794" src="https://inducesmile.com/wp-content/uploads/2015/05/navieight.jpg" alt="navieight" srcset="https://inducesmile.com/wp-content/uploads/2015/05/navieight.jpg 720w, https://inducesmile.com/wp-content/uploads/2015/05/navieight-300x229.jpg 300w" sizes="(max-width: 720px) 100vw, 720px"></a></p><div class="code-block code-block-3" style="margin: 8px 0 8px 8px; float: right;"> <script async="" src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script> <!-- Android 336 --> <ins class="adsbygoogle" style="display:inline-block;width:336px;height:280px" data-ad-client="ca-pub-9110071522046005" data-ad-slot="4417474904"></ins> <script>(adsbygoogle = window.adsbygoogle || []).push({});</script></div><p>The result we want to achieve is to extend what we have already done and to go further to add a Header View in our navigation drawer. The final result will look like the image below.</p><p><a href="https://inducesmile.com/wp-content/uploads/2015/05/headerview.jpg"><img class="alignnone size-full wp-image-806" src="https://inducesmile.com/wp-content/uploads/2015/05/headerview.jpg" alt="Android Material Design Navigation Drawer With Header View" srcset="https://inducesmile.com/wp-content/uploads/2015/05/headerview.jpg 465w, https://inducesmile.com/wp-content/uploads/2015/05/headerview-170x300.jpg 170w" sizes="(max-width: 465px) 100vw, 465px"></a></p><p>You can proceed with creating a new android project or you can download the <i><b><a href="https://inducesmile.com/android/android-navigation-drawer-with-material-design/" target="_blank">Android Navigation Drawer with Material Design</a> </b></i>tutorial source code and import it in your android IDE.</p><p>Once you have done setting up the project, the first thing we will add is the CircularImageView dependency library. This will afford us the possibility to convert the profile image we will use in the HeaderView to a circular ImageView.</p><p>Open your project <strong>build.gradle</strong> file and update the dependencies as below</p><pre class="hljs nginx"><code class="hljs default"><span class="hljs-section">dependencies</span> {
    <span class="hljs-attribute">compile</span> fileTree(dir: <span class="hljs-string">'libs'</span>, include: [<span class="hljs-string">'*.jar'</span>])
    compile <span class="hljs-string">'com.android.support:appcompat-v7:21.0.3'</span>
    compile <span class="hljs-string">'de.hdodenhof:circleimageview:1.2.1'</span>
}
</code></pre><p>In other to add a Header View in the List drawer, we are going to create a layout that we will inflate in other to attach it to our ListView object.</p><p>The layout file will contain one circular ImageView and three Text views.</p><p>Please make sure to add the Header View to the ListVeiw object using the <span class="lang:default decode:true  crayon-inline ">addHeaderView()</span>&nbsp;&nbsp;method before calling <span class="lang:default decode:true  crayon-inline ">setAdapter()</span>&nbsp;&nbsp;method of the ListView class.</p><p>The layout file code snippet is as shown. Copy and paste the code on your project.</p><pre class="hljs xml"><code class="hljs default"><span class="php"><span class="hljs-meta">&lt;?</span>xml version=<span class="hljs-string">"1.0"</span> encoding=<span class="hljs-string">"utf-8"</span><span class="hljs-meta">?&gt;</span></span>
<span class="hljs-tag">&lt;<span class="hljs-name">RelativeLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"200dp"</span>
    <span class="hljs-attr">android:background</span>=<span class="hljs-string">"@drawable/header"</span> &gt;</span>

    <span class="hljs-tag">&lt;<span class="hljs-name">de.hdodenhof.circleimageview.CircleImageView</span>
        <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@+id/imageView"</span>
        <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"24dp"</span>
        <span class="hljs-attr">android:layout_centerHorizontal</span>=<span class="hljs-string">"true"</span>
        <span class="hljs-attr">android:src</span>=<span class="hljs-string">"@drawable/face"</span>
        <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/circleView"</span>
    /&gt;</span>

    <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
        <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/profile_name"</span>
        <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/profile_name"</span>
        <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@+id/circleView"</span>
        <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"16dp"</span>
        <span class="hljs-attr">android:textColor</span>=<span class="hljs-string">"@color/accent_color"</span>
        <span class="hljs-attr">android:textSize</span>=<span class="hljs-string">"14sp"</span>
        <span class="hljs-attr">android:layout_centerHorizontal</span>=<span class="hljs-string">"true"</span> /&gt;</span>

    <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
        <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/profile_address"</span>
        <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/profile_address"</span>
        <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@+id/profile_name"</span>
        <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"16dp"</span>
        <span class="hljs-attr">android:textColor</span>=<span class="hljs-string">"@color/black_color"</span>
        <span class="hljs-attr">android:layout_centerHorizontal</span>=<span class="hljs-string">"true"</span> /&gt;</span>

    <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
        <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
        <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/profile_email"</span>
        <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/profile_email"</span>
        <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"16dp"</span>
        <span class="hljs-attr">android:textColor</span>=<span class="hljs-string">"@color/black_color"</span>
        <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@+id/profile_address"</span>
        <span class="hljs-attr">android:layout_centerHorizontal</span>=<span class="hljs-string">"true"</span> /&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">RelativeLayout</span>&gt;</span>
</code></pre><p>Now that we have done with the layout, we will open the MainActivity.java file and add the following lines of code on it.</p><pre class="hljs javascript"><code class="hljs default">LayoutInflater inflater = getLayoutInflater();

View listHeaderView = inflater.inflate(R.layout.header_list,<span class="hljs-literal">null</span>, <span class="hljs-literal">false</span>);

mDrawerList.addHeaderView(listHeaderView);</code></pre><p>What we have done here is to get a handler for the LayoutInflater. Subsequently we will inflate the header_list.xml layout file and assign it to a View.</p><p>Then we will call the addHeaderView() method of the ListView class and we will pass our view handler as a parameter.</p><p>The complete code for this class is as shown below.</p><pre class="hljs java"><code class="hljs default"><span class="hljs-keyword">package</span> inducesmile.com.androidnavigation;

<span class="hljs-keyword">import</span> android.content.res.Configuration;
<span class="hljs-keyword">import</span> android.os.Bundle;
<span class="hljs-keyword">import</span> android.support.v4.app.Fragment;
<span class="hljs-keyword">import</span> android.support.v4.app.FragmentManager;
<span class="hljs-keyword">import</span> android.support.v4.widget.DrawerLayout;
<span class="hljs-keyword">import</span> android.support.v7.app.ActionBarActivity;
<span class="hljs-keyword">import</span> android.support.v7.app.ActionBarDrawerToggle;
<span class="hljs-keyword">import</span> android.support.v7.widget.Toolbar;
<span class="hljs-keyword">import</span> android.view.LayoutInflater;
<span class="hljs-keyword">import</span> android.view.Menu;
<span class="hljs-keyword">import</span> android.view.MenuItem;
<span class="hljs-keyword">import</span> android.view.View;
<span class="hljs-keyword">import</span> android.widget.AdapterView;
<span class="hljs-keyword">import</span> android.widget.ListView;
<span class="hljs-keyword">import</span> android.widget.Toast;

<span class="hljs-keyword">import</span> java.util.ArrayList;
<span class="hljs-keyword">import</span> java.util.List;


<span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">ActionBarActivity</span> </span>{

    <span class="hljs-keyword">private</span> DrawerLayout mDrawerLayout;
    <span class="hljs-keyword">private</span> ListView mDrawerList;
    String[]titles = {<span class="hljs-string">"Nigeria"</span>, <span class="hljs-string">"Ghana"</span>, <span class="hljs-string">"Senegal"</span>, <span class="hljs-string">"Togo"</span>};
    <span class="hljs-keyword">private</span> CharSequence mTitle;
    <span class="hljs-keyword">private</span> CharSequence mDrawerTitle;
    <span class="hljs-keyword">private</span> ActionBarDrawerToggle mDrawerToggle;
    <span class="hljs-keyword">private</span> Toolbar topToolBar;

    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
        <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mTitle = mDrawerTitle = getTitle();

        topToolBar = (Toolbar)findViewById(R.id.toolbar);
        setSupportActionBar(topToolBar);
        topToolBar.setLogo(R.drawable.logo);
        topToolBar.setLogoDescription(getResources().getString(R.string.logo_desc));

        mDrawerLayout = (DrawerLayout) findViewById(R.id.drawer_layout);
        mDrawerList = (ListView) findViewById(R.id.left_drawer);
        LayoutInflater inflater = getLayoutInflater();
        View listHeaderView = inflater.inflate(R.layout.header_list,<span class="hljs-keyword">null</span>, <span class="hljs-keyword">false</span>);

        mDrawerList.addHeaderView(listHeaderView);

        List&lt;ItemObject&gt; listViewItems = <span class="hljs-keyword">new</span> ArrayList&lt;ItemObject&gt;();
        listViewItems.add(<span class="hljs-keyword">new</span> ItemObject(<span class="hljs-string">"Nigeria"</span>, R.drawable.imageone));
        listViewItems.add(<span class="hljs-keyword">new</span> ItemObject(<span class="hljs-string">"Ghana"</span>, R.drawable.imagetwo));
        listViewItems.add(<span class="hljs-keyword">new</span> ItemObject(<span class="hljs-string">"Senegal"</span>, R.drawable.imagethree));
        listViewItems.add(<span class="hljs-keyword">new</span> ItemObject(<span class="hljs-string">"Togo"</span>, R.drawable.imagefour));

        mDrawerList.setAdapter(<span class="hljs-keyword">new</span> CustomAdapter(<span class="hljs-keyword">this</span>, listViewItems));

        mDrawerToggle = <span class="hljs-keyword">new</span> ActionBarDrawerToggle(MainActivity.<span class="hljs-keyword">this</span>, mDrawerLayout, R.string.drawer_open, R.string.drawer_close) {

            <span class="hljs-comment">/** Called when a drawer has settled in a completely closed state. */</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onDrawerClosed</span><span class="hljs-params">(View view)</span> </span>{
                <span class="hljs-keyword">super</span>.onDrawerClosed(view);
                getSupportActionBar().setTitle(mTitle);
                invalidateOptionsMenu(); <span class="hljs-comment">// creates call to onPrepareOptionsMenu()</span>
            }

            <span class="hljs-comment">/** Called when a drawer has settled in a completely open state. */</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onDrawerOpened</span><span class="hljs-params">(View drawerView)</span> </span>{
                <span class="hljs-keyword">super</span>.onDrawerOpened(drawerView);
                getSupportActionBar().setTitle(mDrawerTitle);
                invalidateOptionsMenu(); <span class="hljs-comment">// creates call to onPrepareOptionsMenu()</span>
            }
        };

        <span class="hljs-comment">// Set the drawer toggle as the DrawerListener</span>
        mDrawerLayout.setDrawerListener(mDrawerToggle);
        mDrawerToggle.setDrawerIndicatorEnabled(<span class="hljs-keyword">true</span>);

        getSupportActionBar().setDisplayHomeAsUpEnabled(<span class="hljs-keyword">true</span>);
        getSupportActionBar().setHomeButtonEnabled(<span class="hljs-keyword">true</span>);

        mDrawerList.setOnItemClickListener(<span class="hljs-keyword">new</span> AdapterView.OnItemClickListener() {
            <span class="hljs-meta">@Override</span>
            <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onItemClick</span><span class="hljs-params">(AdapterView&lt;?&gt; parent, View view, <span class="hljs-keyword">int</span> position, <span class="hljs-keyword">long</span> id)</span> </span>{
                <span class="hljs-comment">// make Toast when click</span>
                Toast.makeText(getApplicationContext(), <span class="hljs-string">"Position "</span> + position, Toast.LENGTH_LONG).show();
                selectItemFragment(position);
            }
        });
    }

    <span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">selectItemFragment</span><span class="hljs-params">(<span class="hljs-keyword">int</span> position)</span></span>{

        Fragment fragment = <span class="hljs-keyword">null</span>;
        FragmentManager fragmentManager = getSupportFragmentManager();
        <span class="hljs-keyword">switch</span>(position) {
            <span class="hljs-keyword">default</span>:
            <span class="hljs-keyword">case</span> <span class="hljs-number">0</span>:
                fragment = <span class="hljs-keyword">new</span> DefaultFragment();
                <span class="hljs-keyword">break</span>;
            <span class="hljs-keyword">case</span> <span class="hljs-number">1</span>:
                fragment = <span class="hljs-keyword">new</span> DefaultFragment();
                <span class="hljs-keyword">break</span>;
            <span class="hljs-keyword">case</span> <span class="hljs-number">2</span>:
                fragment = <span class="hljs-keyword">new</span> DefaultFragment();
                <span class="hljs-keyword">break</span>;
            <span class="hljs-keyword">case</span> <span class="hljs-number">3</span>:
                fragment = <span class="hljs-keyword">new</span> DefaultFragment();
                <span class="hljs-keyword">break</span>;
        }
        fragmentManager.beginTransaction().replace(R.id.main_fragment_container, fragment).commit();

        mDrawerList.setItemChecked(position, <span class="hljs-keyword">true</span>);
        setTitle(titles[position]);
        mDrawerLayout.closeDrawer(mDrawerList);
    }
    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">setTitle</span><span class="hljs-params">(CharSequence title)</span> </span>{
        mTitle = title;
        getSupportActionBar().setTitle(mTitle);
    }

    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onPostCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
        <span class="hljs-keyword">super</span>.onPostCreate(savedInstanceState);
        <span class="hljs-comment">// Sync the toggle state after onRestoreInstanceState has occurred.</span>
        mDrawerToggle.syncState();
    }

    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onConfigurationChanged</span><span class="hljs-params">(Configuration newConfig)</span> </span>{
        <span class="hljs-keyword">super</span>.onConfigurationChanged(newConfig);
        mDrawerToggle.onConfigurationChanged(newConfig);
    }

    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">onCreateOptionsMenu</span><span class="hljs-params">(Menu menu)</span> </span>{
        <span class="hljs-comment">// Inflate the menu; this adds items to the action bar if it is present.</span>
        getMenuInflater().inflate(R.menu.menu_main, menu);
        <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
    }
    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">onPrepareOptionsMenu</span><span class="hljs-params">(Menu menu)</span> </span>{
        <span class="hljs-comment">// If the nav drawer is open, hide action items related to the content view</span>
        <span class="hljs-keyword">boolean</span> drawerOpen = mDrawerLayout.isDrawerOpen(mDrawerList);
        <span class="hljs-keyword">return</span> <span class="hljs-keyword">super</span>.onPrepareOptionsMenu(menu);
    }

    <span class="hljs-meta">@Override</span>
    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">boolean</span> <span class="hljs-title">onOptionsItemSelected</span><span class="hljs-params">(MenuItem item)</span> </span>{
        <span class="hljs-comment">// Handle action bar item clicks here. The action bar will</span>
        <span class="hljs-comment">// automatically handle clicks on the Home/Up button, so long</span>
        <span class="hljs-comment">// as you specify a parent activity in AndroidManifest.xml.</span>
        <span class="hljs-keyword">int</span> id = item.getItemId();

        <span class="hljs-comment">//noinspection SimplifiableIfStatement</span>
        <span class="hljs-keyword">if</span> (id == R.id.action_settings) {
            <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
        }
        <span class="hljs-keyword">if</span> (mDrawerToggle.onOptionsItemSelected(item)) {
            <span class="hljs-keyword">return</span> <span class="hljs-keyword">true</span>;
        }

        <span class="hljs-keyword">return</span> <span class="hljs-keyword">super</span>.onOptionsItemSelected(item);
    }
}
</code></pre><p>Now, when you run your application you will see the interface that looks similar to the sample that was shown earlier on.</p><p>You can download the code for this tutorial below. If you are having hard time downloading the tutorials, kindly contact me.</p><div class="w3eden"><!-- WPDM Link Template: Default Template --><div class="wpdm-link-tpl link-btn [color]" data-durl="https://inducesmile.com/download/android-material-design-navigation-drawer-with-header-view/?wpdmdl=808"><div class="media"><div class="pull-left"><img class="wpdm_icon" alt="Icon" src="https://inducesmile.com/wp-content/plugins/download-manager/assets/file-type-icons/zip.svg" onerror="this.src=&quot;https://inducesmile.com/wp-content/plugins/download-manager/assets/file-type-icons/unknown.svg&quot;;"></div><div class="media-body"><strong class="ptitle">Android Material Design Navigation Drawer With Header View <span class="label label-default" style="font-weight: 400;">5.83 MB</span></strong><div><strong><a class="wpdm-download-link [btnclass]" rel="nofollow" href="#" onclick="location.href='https://inducesmile.com/download/android-material-design-navigation-drawer-with-header-view/?wpdmdl=808';return false;">Download</a></strong></div></div></div></div><div style="clear: both"></div></div><p><span style="color: #000000;">Remember to subscribe with your email so that you will be among the first to receive our new post once it is published </span></p> <script type="text/javascript">jQuery(document).ready(function($) {
                $.post('https://inducesmile.com/wp-admin/admin-ajax.php', {action: 'mts_view_count', id: '805'});
            });</script><div class="relpost-thumb-wrapper relpost-align-left "><h3>OTHER INTERESTING POSTS:</h3><div style="clear: both"></div><div class="relpost-block-container"><a class="relpost-block-single" href="https://inducesmile.com/android/what-kind-of-mobile-apps-do-nigerians-like/"><div style="width: 150px; height: 225px;"><div class="relpost-block-single-image" alt="Android Expandable ListView Example Tutorial" style=" background: transparent url(https://inducesmile.com/wp-content/uploads/2014/12/mobileapp-150x150.jpg) no-repeat scroll 0% 0%; width: 150px; height: 150px; "></div><div class="relpost-block-single-text" style="font-family: ;  font-size: 12px;  color: #333333;">What kind of mobile apps do Nigerians like?</div></div></a><a class="relpost-block-single" href="https://inducesmile.com/android/android-dictionary-application-with-search-suggest-and-text-to-speech/"><div style="width: 150px; height: 225px;"><div class="relpost-block-single-image" alt="How to fix android.support.v7.actionbaractivity is deprecated" style=" background: transparent url(https://inducesmile.com/wp-content/uploads/2015/04/dictionaryapp-150x150.jpg) no-repeat scroll 0% 0%; width: 150px; height: 150px; "></div><div class="relpost-block-single-text" style="font-family: ;  font-size: 12px;  color: #333333;">Android Dictionary Application with Search Suggest and Text to Speech Feature</div></div></a><a class="relpost-block-single" href="https://inducesmile.com/android/play-youtube-video-in-android-using-youtube-player-api/"><div style="width: 150px; height: 225px;"><div class="relpost-block-single-image" alt="Play YouTube video in Android using YouTube player API" style=" background: transparent url(https://inducesmile.com/wp-content/uploads/2015/04/youtubedataapi-150x150.jpg) no-repeat scroll 0% 0%; width: 150px; height: 150px; "></div><div class="relpost-block-single-text" style="font-family: ;  font-size: 12px;  color: #333333;">Play YouTube video in Android using YouTube player API</div></div></a><a class="relpost-block-single" href="https://inducesmile.com/android/android-torch-light-flash-light-app-tutorial/"><div style="width: 150px; height: 225px;"><div class="relpost-block-single-image" alt="Android Torch Light / Flash Light App Tutorial" style=" background: transparent url(https://inducesmile.com/wp-content/uploads/2015/04/torchlight-150x150.jpg) no-repeat scroll 0% 0%; width: 150px; height: 150px; "></div><div class="relpost-block-single-text" style="font-family: ;  font-size: 12px;  color: #333333;">Android Torch Light / Flash Light App Tutorial</div></div></a><a class="relpost-block-single" href="https://inducesmile.com/android/how-to-get-android-screen-size-in-pixels-and-inches-programmatically/"><div style="width: 150px; height: 225px;"><div class="relpost-block-single-image" alt="How to get Android Screen Size in pixels and inches programmatically" style=" background: transparent url(https://inducesmile.com/wp-content/uploads/2015/09/screensize-150x150.jpg) no-repeat scroll 0% 0%; width: 150px; height: 150px; "></div><div class="relpost-block-single-text" style="font-family: ;  font-size: 12px;  color: #333333;">How to get Android Screen Size in pixels and inches programmatically</div></div></a><a class="relpost-block-single" href="https://inducesmile.com/android/android-butter-knife-view-binding-example/"><div style="width: 150px; height: 225px;"><div class="relpost-block-single-image" alt="android butter knife view" style=" background: transparent url(https://inducesmile.com/wp-content/uploads/2016/11/androidbutterknifebind-150x150.jpg) no-repeat scroll 0% 0%; width: 150px; height: 150px; "></div><div class="relpost-block-single-text" style="font-family: ;  font-size: 12px;  color: #333333;">Android Butter Knife Example</div></div></a></div><div style="clear: both"></div></div></div> <!-- Start Share Buttons --><div class="shareit floating"> <!-- Facebook Share--> <span class="share-item facebooksharebtn"><div class="fb-share-button fb_iframe_widget" data-layout="button_count" fb-xfbml-state="rendered" fb-iframe-plugin-query="app_id=&amp;container_width=100&amp;href=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;layout=button_count&amp;locale=en_US&amp;sdk=joey"><span style="vertical-align: bottom; width: 69px; height: 20px;"><iframe name="f9287751b3773c" width="1000px" height="1000px" frameborder="0" allowtransparency="true" allowfullscreen="true" scrolling="no" allow="encrypted-media" title="fb:share_button Facebook Social Plugin" src="https://www.facebook.com/v2.4/plugins/share_button.php?app_id=&amp;channel=https%3A%2F%2Fstaticxx.facebook.com%2Fconnect%2Fxd_arbiter%2Fr%2FEIL5DcDc3Zh.js%3Fversion%3D42%23cb%3Df17ac16ac516a7c%26domain%3Dinducesmile.com%26origin%3Dhttps%253A%252F%252Finducesmile.com%252Ff5af30cfe0047%26relation%3Dparent.parent&amp;container_width=100&amp;href=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;layout=button_count&amp;locale=en_US&amp;sdk=joey" style="border: none; visibility: visible; width: 69px; height: 20px;" class=""></iframe></span></div> </span> <!-- Facebook --> <span class="share-item facebookbtn"><div id="fb-root" class=" fb_reset"><div style="position: absolute; top: -10000px; height: 0px; width: 0px;"><div><iframe name="fb_xdm_frame_https" frameborder="0" allowtransparency="true" allowfullscreen="true" scrolling="no" allow="encrypted-media" id="fb_xdm_frame_https" aria-hidden="true" title="Facebook Cross Domain Communication Frame" tabindex="-1" src="https://staticxx.facebook.com/connect/xd_arbiter/r/EIL5DcDc3Zh.js?version=42#channel=f5af30cfe0047&amp;origin=https%3A%2F%2Finducesmile.com" style="border: none;"></iframe></div></div><div style="position: absolute; top: -10000px; height: 0px; width: 0px;"><div></div></div></div><div class="fb-like fb_iframe_widget" data-send="false" data-layout="button_count" data-width="150" data-show-faces="false" fb-xfbml-state="rendered" fb-iframe-plugin-query="app_id=&amp;container_width=100&amp;href=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;layout=button_count&amp;locale=en_US&amp;sdk=joey&amp;send=false&amp;show_faces=false&amp;width=150"><span style="vertical-align: bottom; width: 61px; height: 20px;"><iframe name="f2a47b92b5ada8" width="150px" height="1000px" frameborder="0" allowtransparency="true" allowfullscreen="true" scrolling="no" allow="encrypted-media" title="fb:like Facebook Social Plugin" src="https://www.facebook.com/v2.4/plugins/like.php?app_id=&amp;channel=https%3A%2F%2Fstaticxx.facebook.com%2Fconnect%2Fxd_arbiter%2Fr%2FEIL5DcDc3Zh.js%3Fversion%3D42%23cb%3Df1909dccea39028%26domain%3Dinducesmile.com%26origin%3Dhttps%253A%252F%252Finducesmile.com%252Ff5af30cfe0047%26relation%3Dparent.parent&amp;container_width=100&amp;href=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;layout=button_count&amp;locale=en_US&amp;sdk=joey&amp;send=false&amp;show_faces=false&amp;width=150" style="border: none; visibility: visible; width: 61px; height: 20px;" class=""></iframe></span></div> </span> <!-- Twitter --> <span class="share-item twitterbtn"> <iframe id="twitter-widget-0" scrolling="no" frameborder="0" allowtransparency="true" class="twitter-share-button twitter-share-button-rendered twitter-tweet-button" title="Twitter Tweet Button" src="https://platform.twitter.com/widgets/tweet_button.ed3aa96ee3d5c426af8aa717469ea983.en.html#dnt=false&amp;id=twitter-widget-0&amp;lang=en&amp;original_referer=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;size=m&amp;text=Android%20Material%20Design%20Navigation%20Drawer%20With%20Header%20View&amp;time=1528504663716&amp;type=share&amp;url=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F" style="position: static; visibility: visible; width: 63px; height: 20px;"></iframe> </span> <!-- GPlus --> <span class="share-item gplusbtn"> <div id="___plusone_0" style="text-indent: 0px; margin: 0px; padding: 0px; background: transparent; border-style: none; float: none; line-height: normal; font-size: 1px; vertical-align: baseline; display: inline-block; width: 32px; height: 20px;"><iframe ng-non-bindable="" frameborder="0" hspace="0" marginheight="0" marginwidth="0" scrolling="no" style="position: static; top: 0px; width: 32px; margin: 0px; border-style: none; left: 0px; visibility: visible; height: 20px;" tabindex="0" vspace="0" width="100%" id="I0_1528504663516" name="I0_1528504663516" src="https://apis.google.com/u/0/se/0/_/+1/fastbutton?usegapi=1&amp;size=medium&amp;origin=https%3A%2F%2Finducesmile.com&amp;url=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;gsrc=3p&amp;ic=1&amp;jsh=m%3B%2F_%2Fscs%2Fapps-static%2F_%2Fjs%2Fk%3Doz.gapi.en_GB.EY9SNuu1tus.O%2Fm%3D__features__%2Fam%3DQQE%2Frt%3Dj%2Fd%3D1%2Frs%3DAGLTcCMTCLxzTfe26_cJV6o9D1Vw9f7Izw#_methods=onPlusOne%2C_ready%2C_close%2C_open%2C_resizeMe%2C_renderstart%2Concircled%2Cdrefresh%2Cerefresh&amp;id=I0_1528504663516&amp;_gfid=I0_1528504663516&amp;parent=https%3A%2F%2Finducesmile.com&amp;pfname=&amp;rpctoken=16801800" data-gapiattached="true" title="G+"></iframe></div> </span> <!-- Pinterest --> <span class="share-item pinbtn"> <a class="PIN_1528504663963_button_pin PIN_1528504663963_save" href="https://uk.pinterest.com/pin/create/button/?guid=5oif1yjVaVTN-1&amp;url=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;media=https%3A%2F%2Finducesmile.com%2Fwp-content%2Fuploads%2F2015%2F05%2Fbanner.jpg&amp;description=Android%20Material%20Design%20Navigation%20Drawer%20With%20Header%20View" data-pin-log="button_pinit" data-pin-href="https://uk.pinterest.com/pin/create/button/?guid=5oif1yjVaVTN-1&amp;url=https%3A%2F%2Finducesmile.com%2Fandroid%2Fandroid-material-design-navigation-drawer-with-header-view%2F&amp;media=https%3A%2F%2Finducesmile.com%2Fwp-content%2Fuploads%2F2015%2F05%2Fbanner.jpg&amp;description=Android%20Material%20Design%20Navigation%20Drawer%20With%20Header%20View">Save</a> </span></div> <!-- end Share Buttons --></div><!--.post-single-content--></div>
