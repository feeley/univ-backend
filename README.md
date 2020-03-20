# univ-backend
Experiments with the Gambit universal backend

Gambit's universal backend can compile the Gambit interpreter with much of the same functionnality.  Here we have done it for JavaScript (gsi-js) and Python (gsi-py).  They can be invoked like this :

    % node gsi-js <normal-command-line-arguments>
    % python2 gsi-py <normal-command-line-arguments>
    % python3 gsi-py <normal-command-line-arguments>

Here is a demo:

    % node gsi-js -v
    v4.9.3 20200101213000 unknown-system-type "./configure"
    % node gsi-js . fib
    (time (fib 30))
        2.131000 secs real time
        2.131000 secs cpu time (2.131000 user, 0.000000 system)
        no collections
        no bytes allocated
        no minor faults
        no major faults
    832040
    % ls
    README.md	fib.scm		gsi-js		gsi-py
    % node gsi-js
    Gambit v4.9.3
    
    > (apropos 'shell)
    "##" namespace:
      get-shell-program, os-shell-command, shell-args-numbered, shell-command,
      shell-command-blocking, shell-install-dirs, shell-var-binding,
      shell-var-bindings
    empty namespace:
      shell-command, user-info-shell
    > (##os-shell-command "ls")
    README.md
    fib.scm
    gsi-js
    gsi-py
    0
    > (file-info "fib.scm")
    #<file-info #2
       type: regular
       device: 16777221
       inode: 11159611
       mode: 33188
       number-of-links: 1
       owner: 501
       group: 20
       size: 100
       last-access-time: #<time #3>
       last-modification-time: #<time #4>
       last-change-time: #<time #5>
       attributes: 0
       creation-time: #<time #6>>
    > (expt 2 1000)
    10715086071862673209484250490600018105614048117055336074437503883703510511249361224931983788156958581275946729175531468251871452856923140435984577574698574803934567774824230985421074605062371141877954182153046474983581941267398767559165543946077062914571196477686542167660429831652624386837205668069376
    > (define (date) (host-expression "g_host2scm(new Date().toString())"))
    > (date)
    "Fri Mar 20 2020 17:06:45 GMT-0400 (GMT-04:00)"
    > (define (Array n) (host-expression "g_host2scm(Array(g_scm2host(@1@)))" n))
    > (Array 5)
    #(#!void #!void #!void #!void #!void)
    > ,q
