---
id: version-0.46-permissionsandroid
title: permissionsandroid
original_id: permissionsandroid
---
<a id="content"></a><h1><a class="anchor" name="permissionsandroid"></a>PermissionsAndroid <a class="hash-link" href="docs/permissionsandroid.html#permissionsandroid">#</a></h1><div><div><span><div class="banner-crna-ejected">
  <h3>Project with Native Code Required</h3>
  <p>
    This API only works in projects made with <code>react-native init</code>
    or in those made with Create React Native App which have since ejected. For
    more information about ejecting, please see
    the <a href="https://github.com/react-community/create-react-native-app/blob/master/EJECTING.md" target="_blank">guide</a> on
    the Create React Native App repository.
  </p>
</div>

</span><p><code>PermissionsAndroid</code> provides access to Android M's new permissions model.
Some permissions are granted by default when the application is installed
so long as they appear in <code>AndroidManifest.xml</code>. However, "dangerous"
permissions require a dialog prompt. You should use this module for those
permissions.</p><p>On devices before SDK version 23, the permissions are automatically granted
if they appear in the manifest, so <code>check</code> and <code>request</code>
should always be true.</p><p>If a user has previously turned off a permission that you prompt for, the OS
will advise your app to show a rationale for needing the permission. The
optional <code>rationale</code> argument will show a dialog prompt only if
necessary - otherwise the normal permission prompt will appear.</p><h3><a class="anchor" name="example"></a>Example <a class="hash-link" href="docs/permissionsandroid.html#example">#</a></h3><div class="prism language-javascript"><span class="token keyword">async</span> <span class="token keyword">function</span> <span class="token function">requestCameraPermission</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">try</span> <span class="token punctuation">{</span>
    <span class="token keyword">const</span> granted <span class="token operator">=</span> <span class="token keyword">await</span> PermissionsAndroid<span class="token punctuation">.</span><span class="token function">request</span><span class="token punctuation">(</span>
      PermissionsAndroid<span class="token punctuation">.</span>PERMISSIONS<span class="token punctuation">.</span>CAMERA<span class="token punctuation">,</span>
      <span class="token punctuation">{</span>
        <span class="token string">'title'</span><span class="token punctuation">:</span> <span class="token string">'Cool Photo App Camera Permission'</span><span class="token punctuation">,</span>
        <span class="token string">'message'</span><span class="token punctuation">:</span> <span class="token string">'Cool Photo App needs access to your camera '</span> <span class="token operator">+</span>
                   <span class="token string">'so you can take awesome pictures.'</span>
      <span class="token punctuation">}</span>
    <span class="token punctuation">)</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>granted <span class="token operator">===</span> PermissionsAndroid<span class="token punctuation">.</span>RESULTS<span class="token punctuation">.</span>GRANTED<span class="token punctuation">)</span> <span class="token punctuation">{</span>
      console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"You can use the camera"</span><span class="token punctuation">)</span>
    <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
      console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"Camera permission denied"</span><span class="token punctuation">)</span>
    <span class="token punctuation">}</span>
  <span class="token punctuation">}</span> <span class="token keyword">catch</span> <span class="token punctuation">(</span><span class="token class-name">err</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    console<span class="token punctuation">.</span><span class="token function">warn</span><span class="token punctuation">(</span>err<span class="token punctuation">)</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span></div></div><span><h3><a class="anchor" name="methods"></a>Methods <a class="hash-link" href="docs/permissionsandroid.html#methods">#</a></h3><div class="props"><div class="prop"><h4 class="methodTitle"><a class="anchor" name="constructor"></a>constructor<span class="methodType">()</span> <a class="hash-link" href="docs/permissionsandroid.html#constructor">#</a></h4></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="checkpermission"></a>checkPermission<span class="methodType">(permission)</span> <a class="hash-link" href="docs/permissionsandroid.html#checkpermission">#</a></h4><div><p>DEPRECATED - use check</p><p>Returns a promise resolving to a boolean value as to whether the specified
permissions has been granted</p><p>@deprecated</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="check"></a>check<span class="methodType">(permission)</span> <a class="hash-link" href="docs/permissionsandroid.html#check">#</a></h4><div><p>Returns a promise resolving to a boolean value as to whether the specified
permissions has been granted</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="requestpermission"></a>requestPermission<span class="methodType">(permission, rationale?)</span> <a class="hash-link" href="docs/permissionsandroid.html#requestpermission">#</a></h4><div><p>DEPRECATED - use request</p><p>Prompts the user to enable a permission and returns a promise resolving to a
boolean value indicating whether the user allowed or denied the request</p><p>If the optional rationale argument is included (which is an object with a
<code>title</code> and <code>message</code>), this function checks with the OS whether it is
necessary to show a dialog explaining why the permission is needed
(<a href="https://developer.android.com/training/permissions/requesting.html#explain">https://developer.android.com/training/permissions/requesting.html#explain</a>)
and then shows the system permission dialog</p><p>@deprecated</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="request"></a>request<span class="methodType">(permission, rationale?)</span> <a class="hash-link" href="docs/permissionsandroid.html#request">#</a></h4><div><p>Prompts the user to enable a permission and returns a promise resolving to a
string value indicating whether the user allowed or denied the request</p><p>If the optional rationale argument is included (which is an object with a
<code>title</code> and <code>message</code>), this function checks with the OS whether it is
necessary to show a dialog explaining why the permission is needed
(<a href="https://developer.android.com/training/permissions/requesting.html#explain">https://developer.android.com/training/permissions/requesting.html#explain</a>)
and then shows the system permission dialog</p></div></div><div class="prop"><h4 class="methodTitle"><a class="anchor" name="requestmultiple"></a>requestMultiple<span class="methodType">(permissions)</span> <a class="hash-link" href="docs/permissionsandroid.html#requestmultiple">#</a></h4><div><p>Prompts the user to enable multiple permissions in the same dialog and
returns an object with the permissions as keys and strings as values
indicating whether the user allowed or denied the request</p></div></div></div></span></div><p class="edit-page-block"><a target="_blank" href="https://github.com/facebook/react-native/blob/master/Libraries/PermissionsAndroid/PermissionsAndroid.js">Improve this page</a> by sending a pull request!</p><div class="docs-prevnext"><a class="docs-prev" href="docs/panresponder.html#content">← Prev</a><a class="docs-next" href="docs/pixelratio.html#content">Next →</a></div>