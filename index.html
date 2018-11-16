<!DOCTYPE html>
<html>
  <head>
    <title>Video file streaming</title>
    <meta charset="utf-8" />
    <link rel="stylesheet" href="./style/style.css" />
    <link rel="icon" sizes="200x200" type="image/png" href="./style/play.png">
    <link href="https://fonts.googleapis.com/css?family=Ubuntu" rel="stylesheet" type="text/css">
    <link href="https://fonts.googleapis.com/css?family=Poppins" rel="stylesheet" type="text/css">
  </head>
  <body>
    <nav class="topnav">
    <a id="home" href="./index.html">Home</a> 
    <a id="login">Log in</a>
    <a id="connect">Disconnect</a>
</nav>
    <div style="line-height:10px">
    <a href="./index.html"><img id="reader" src="./style/tv.png" width = 90px style='float: left;'/></a>
    <h1><span class="black"><a href="./index.html">m3u</a></span></h1>
    <h1><a href="./index.html"><span class="grey">Google</span> <span class="grey-light">Drive</span></a></h1>
    </div>
        <h2>Directly from the Cloud</h2>
    <br/>
    <!--Add buttons to initiate auth sequence and sign out-->
    <button type="button" id="auth" enabled>Authenticate</button>
    <div id="result" style="display:none"></div>
    <pre id="content"></pre>

  <a href="#" id="nextPage" style="display: none;" >Ver más &raquo;</a>

    <script type="text/javascript">
      var CLIENT_ID = '983869916425-495k0u2mf6i377r6c04d1nkleek9qbbj.apps.googleusercontent.com';
      var DISCOVERY_DOCS = ["https://www.googleapis.com/discovery/v1/apis/drive/v3/rest"];
      var SCOPES = 'https://www.googleapis.com/auth/drive';
      var pickerApiLoaded = false;
      var API_KEY = 'AIzaSyBa-rF9qjubzf5GM0I5vI847KeXv-0TS5A';
      var PATH="https://www.googleapis.com/drive/v3/files/"
      var q="?alt=media&key=";
      var oauthToken;
      

      var login = document.getElementById('login');
      var connect = document.getElementById('connect');
      var initialized=false;
      function handleClientLoad() {

        gapi.load('client:auth2', initClient);
       <!-- gapi.client.load('drive', 'v3'); -->
       gapi.load('picker', onPickerApiLoad);



      }
       
      function initClient() {
        gapi.client.init({
          clientId: CLIENT_ID,
          discoveryDocs: DISCOVERY_DOCS,
          scope: SCOPES
        }).then(function () {

          // Listen for sign-in state changes.
          gapi.auth2.getAuthInstance().isSignedIn.listen(updateSigninStatus);

          // Handle the initial sign-in state.
          updateSigninStatus(gapi.auth2.getAuthInstance().isSignedIn.get());

          //login.href="javascript:handleAuthClick()";
          
          
          //gapi.auth2.authorize({client_id: CLIENT_ID, scope: SCOPES}, handleAuthResult);
        });
      }

      /**
       *  Called when the signed in status changes, to update the UI
       *  appropriately. After a sign-in, the API is called.
       */
      function updateSigninStatus(isSignedIn) {
        if (isSignedIn) {
          login.href="javascript:handleSignoutClick()";
          login.innerHTML="Log out";
          connect.href="javascript:disconnect()";


         oauthToken = gapi.auth.getToken().access_token;
          
        } 
        else {
          login.href="javascript:handleAuthClick()";
          login.innerHTML="Log in";

        }
      }




      function listFiles(query,nextPageToken="",fileType="",currentLevelFolderList=[],folderList=[]) {
        gapi.client.drive.files.list({
          pageSize: 1000, //no puede ser menor a 4
          'pageToken': nextPageToken,
          includeTeamDrives : true,
          fields: "nextPageToken, files(id, name, mimeType, fileExtension, webContentLink, parents, properties)",
          orderBy:"name,folder",
          q: query
        }).then(function(response) {
          var files = response.result.files.concat(currentLevelFolderList);
          if (response.result.nextPageToken && fileType=="folder"){
            listFiles(query, response.result.nextPageToken, "folder", files);
          }
          else{
            if (files && files.length > 0 && fileType=="video") {
              buildM3U(files,folderList);
            }
            else if (files && files.length > 0) {
              var query;
              for (var i = 0; i < files.length; i++) {
                var file = files[i];
                if (i==0){
                  query="('"+file.id+"' in parents";
                }
                else {
                  query+=" or '"+file.id+"' in parents";
                }         
              }
              query+=") and mimeType='application/vnd.google-apps.folder'";
              files=folderList.concat(files);
              listFiles(query,"","folder",[],files);
            }
            else {
              files=folderList;
              for (var i = 0; i < files.length; i++) {
                var file = files[i];
                if (i==0){
                  query="('"+file.id+"' in parents";
                }
                else {
                  query+=" or '"+file.id+"' in parents";
                }         
              }
              query+=") and (mimeType contains 'video' or mimeType contains 'image')";
              var delayInMilliseconds = 1000; //1 second
              setTimeout(listFiles(query,"","video",[],folderList), delayInMilliseconds); 
              
            }
          }
        });
      }
      
      function buildM3U(files,folderList) {
        var videoFilesTitles={};
        for (var i = 0; i<folderList.length; i++){
          var key=folderList[i].id;
          videoFilesTitles[key]=folderList[i].name;
        }
        var videoFiles={};
        var parents=[];
        var video="";
        var logo="";
        var name="";
        var keys=[];
        for (var i = 0; i < files.length; i++) {
          var file = files[i]; 
          keys = Object.keys(videoFiles);
          if (keys.indexOf(file.parents[0])<0){
            videoFiles[file.parents[0]]={"video":"","title":"","logo":""};
          }
          if (file.mimeType.indexOf("video") != -1) {
            videoFiles[file.parents[0]].video=file.id;
            videoFiles[file.parents[0]].title=videoFilesTitles[file.parents[0]]; 
          } 
          else if (file.mimeType.indexOf("image") != -1) {
            videoFiles[file.parents[0]].logo=file.id;
          }
        }
        buildM3U2(videoFiles);
      }
      function buildM3U2(videoFiles) {
        var keys = Object.keys(videoFiles);
        var video="";
        var logo="";
        var m3u="#EXTM3U"+"\n\n";
        for (var i = 0; i < keys.length; i++) {
          var file = keys[i]; 
          var video=videoFiles[file].video;
          var logo=videoFiles[file].logo;
          var name=videoFiles[file].title;
          if (video!="") {       
            videoLink=PATH + video + q + API_KEY;
            if (logo!="") {
              logoLink=PATH + logo + q + API_KEY;
              m3u+= '#EXTINF:-1 tvg-logo="'+logoLink+'"'+" group-title='Movies' type='video', "+name+"\n" + videoLink + "\n\n\n";
            }
            else {
              m3u+= "#EXTINF:-1 group-title='Movies' type='video', "+name+"\n" + videoLink + "\n\n\n";
            }
          } 

        }
        //document.getElementById('result').style.display = "none";
        document.getElementById('result').innerHTML='<textarea id="m3u" style="display: none"></textarea>';
        document.getElementById("m3u").value=m3u;
        document.getElementById("m3u").style.display="block";
      }

      function onPickerApiLoad() {
        pickerApiLoaded = true;
        var authBtn = document.getElementById('auth');
        //authBtn.disabled = false;
        authBtn.setAttribute("onclick","createPicker()");
      
      }

    function createPicker() {
    if (pickerApiLoaded && oauthToken) {
      document.getElementById('result').style.display = "none";
      var view = new google.picker.DocsView()
              .setOwnedByMe(true)
              .setIncludeFolders(true)
              .setSelectFolderEnabled(true)
              .setMimeTypes('application/vnd.google-apps.folder');
      var picker = new google.picker.PickerBuilder()
              .enableFeature(google.picker.Feature.NAV_HIDDEN)
              .setTitle('Select a folder to use for the playlist')
              .addView(view)
              .setOAuthToken(oauthToken)
              // .setDeveloperKey('AIzaSyAksMFVtrWBKqN2gaDnP29FdpB3omikrQU')
              .setCallback(pickerCallback)
              .build();
      picker.setVisible(true);
    }
      
    else if (pickerApiLoaded) {
      handleAuthClick();
    }
  }


    function pickerCallback(data) {
    if (data.action == google.picker.Action.PICKED) {
      query="'"+data.docs[0].id+"' in parents and mimeType='application/vnd.google-apps.folder'";
      document.getElementById('result').innerHTML = '<img src="./style/loading.gif" class="center" width = 90px>';
      document.getElementById('result').style.display = "block";
      listFiles(query,"","folder",[],data.docs);
    }
  }
      /**
       *  Sign in the user upon button click.
       */
      function handleAuthClick(event) {
        initialized=true;
        gapi.auth2.getAuthInstance().signIn({ux_mode: "redirect"});
      }
      /**
       *  Sign out the user upon button click.
       */
      function handleSignoutClick(event) {
        gapi.auth2.getAuthInstance().signOut().then(function () {
          location.reload();
        }); 
      }
      function disconnect(event) {
        gapi.auth2.getAuthInstance().disconnect().then(function () {
          signoutButton.click();
        });
      }
      
    </script>

    <script async defer src="https://apis.google.com/js/api.js"
      onload="this.onload=function(){};handleClientLoad()"
      onreadystatechange="if (this.readyState === 'complete') this.onload()">
    </script>
  </body>
</html>
