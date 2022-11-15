# minishell
Minishell is a project where you quite literally create a miniature shell using the C language with the following parameters. 

Your shell should:

• Display a prompt when waiting for a new command.

• Have a working history.

• Search and launch the right executable (based on the PATH variable or using a
relative or an absolute path).

• Not use more than one global variable. Think about it. You will have to explain
its purpose.

• Not interpret unclosed quotes or special characters which are not required by the
subject such as \ (backslash) or ; (semicolon).

• Handle ’ (single quote) which should prevent the shell from interpreting the metacharacters in the quoted sequence.

• Handle " (double quote) which should prevent the shell from interpreting the metacharacters in the quoted sequence except for $ (dollar sign).

• Implement redirections:

◦ < should redirect input.

◦ > should redirect output.

◦ << should be given a delimiter, then read the input until a line containing the

delimiter is seen. However, it doesn’t have to update the history!

◦ >> should redirect output in append mode.

• Implement pipes (| character). The output of each command in the pipeline is

connected to the input of the next command via a pipe.

• Handle environment variables ($ followed by a sequence of characters) which

should expand to their values.

• Handle $? which should expand to the exit status of the most recently executed

foreground pipeline.

• Handle ctrl-C, ctrl-D and ctrl-\ which should behave like in bash.

• In interactive mode:

◦ ctrl-C displays a new prompt on a new line.

◦ ctrl-D exits the shell.

◦ ctrl-\ does nothing.

• Your shell must implement the following builtins:

◦ echo with option -n

◦ cd with only a relative or absolute path

◦ pwd with no options

◦ export with no options

◦ unset with no options

◦ env with no options or arguments

◦ exit with no options


# minishell allowed functions (and their very basic definitions) 

**Readline** https://linux.die.net/man/3/readline **very long description, follow reference link."**

 **Rl_clear_history** void rl_clear_history (void) Clear the history list by deleting all of the entries, in the same manner as the History library’s clear_history() function. This differs from clear_history because it frees private data Readline saves in the history list.

 **Rl_on_new_line** int rl_on_new_line (void) Tell the update functions that we have moved onto a new (empty) line, usually after outputting a newline.

 **Rl_replace_line** void rl_replace_line (const char *text, int clear_undo)  Replace the contents of rl_line_buffer with text. The point and mark are preserved, if possible. If clear_undo is non-zero, the undo list associated with the current line is cleared.

 **Rl_redisplay** void rl_redisplay (void) Change what’s displayed on the screen to reflect the current contents of rl_line_buffer.

 **Add_history** void add_history (char *string) Place string at the end of the history list. The associated data field (if any) is set to NULL.

 **Printf** https://www.tutorialspoint.com/c_standard_library/c_function_printf.htm **too long to add in here, use reference page**

 **Malloc** dynamically allocate a single large block of memory with the specified size. It returns a pointer of type void which can be cast into a pointer of any form.

 **Free** void free(void *ptr) deallocates the memory previously allocated by a call to calloc, malloc, or realloc.

 **Write** The write() function shall attempt to write nbyte bytes from the buffer pointed to by buf to the file associated with the open file descriptor, fildes.

 **Access** access() checks whether the calling process can access the file pathname. If pathname is a symbolic link, it is dereferenced.

 **Open** Given a pathname for a file, open() returns a file descriptor, a small, nonnegative integer for use in subsequent system calls (read(2), write(2), lseek(2), fcntl(2), etc.). The file descriptor returned by a successful call will be the lowest-numbered file descriptor not currently open for the process.

 **Read** read() attempts to read up to count bytes from file descriptor fd into the buffer starting at buf.

 **Close** close() closes a file descriptor, so that it no longer refers to any file and may be reused.

 **Fork** Fork system call is used for creating a new process, which is called child process, which runs concurrently with the process that makes the fork() call (parent process).

 **Wait** wait() blocks the calling process until one of its child processes exits or a signal is received. After child process terminates, parent continues its execution after wait system call instruction.
 Waitpid Suspends the calling process until a child process ends or is stopped. More precisely, waitpid() suspends the calling process until the system gets status information on the child. If the system already has status information on an appropriate child when waitpid() is called, waitpid() returns immediately.

 **Wait3** wait3() function delays its caller until a signal is received or one of its child processes terminates or stops due to tracing. If any child process has died or stopped due to tracing and this has not already been reported, return is immediate, returning the process ID and status of one of those children. If that child process has died, it is discarded. If there are no children, -1 is returned immediately. If there are only running or stopped but reported children, the calling process is blocked.

 **Wait4** wait4() function is an extended interface. With a pid argument of 0, it is equivalent to wait3(). If pid has a nonzero value, then wait4() returns status only for the indicated process ID, but not for any other child processes. The status can be evaluated using the macros listed on the wstat() reference page.

 **Signal** signal() sets the disposition of the signal signum to handler,
       which is either SIG_IGN, SIG_DFL, or the address of a programmer-
       defined function (a "signal handler"). ***Recommended not to use, use sigaction.**

 **Sigaction** sigaction() system call is used to change the action taken by
       a process on receipt of a specific signal.

 **Sigemptyset** sigemptyset() initializes the signal set given by set to empty, with all signals excluded from the set.

 **Sigaddset** sigaddset() add signal signum from set.

 **Kill** kill() system call can be used to send any signal to any process group or process.

 **Exit** void exit(int status) terminates the calling process immediately. Any open file descriptors belonging to the process are closed and any children of the process are inherited by process 1, init, and the process parent is sent a SIGCHLD signal.

 **Getcwd** getcwd() function copies an absolute pathname of the current working directory to the array pointed to by buf, which is of length size.

 **Chdir** chdir() changes the current working directory of the calling process to the directory specified in path.

 **Stat** stat() function is used to list properties of a file identified by path . It reads all file properties and dumps to buf structure.

 **Lstat** lstat() function shall be equivalent to stat(), except when path refers to a symbolic link. In that case lstat() shall return information about the link, while stat() shall return information about the file the link references.

 **Fstat** fstat() function gets status information about the object specified by the open descriptor descriptor and stores the information in the area of memory indicated by the buffer argument. The status information is returned in a stat structure, as defined in the <sys/stat.
 Unlink deletes the file name filename . If this is a file's sole name, the file itself is also deleted. (Actually, if any process has the file open when this happens, deletion is postponed until all processes have closed the file.) The function unlink is declared in the header file unistd.

 **Execve** execve() function replaces the current process image with a new process image specified by path . The new image is constructed from a regular, executable file called the new process image file. No return is made because the calling process image is replaced by the new process image.

 **Dup** dup() system call creates a copy of a file descriptor. It uses the lowest-numbered unused descriptor for the new descriptor. If the copy is successfully created, then the original and copy file descriptors may be used interchangeably.

 **Dup2** dup2() system call is similar to dup() but the basic difference between them is that instead of using the lowest-numbered unused file descriptor, it uses the descriptor number specified by the user.

 **Pipe** a connection between two processes, such that the standard output from one process becomes the standard input of the other process. In UNIX Operating System, Pipes are useful for communication between related processes(inter-process communication).

 **Opendir** opendir() function shall open a directory stream corresponding to the directory named by the dirname argument. The directory stream is positioned at the first entry. If the type DIR is implemented using a file descriptor, applications shall only be able to open up to a total of {OPEN_MAX} files and directories.

 **Readdir** readdir() function shall return a pointer to a structure representing the directory entry at the current position in the directory stream specified by the argument dirp, and position the directory stream at the next entry. It shall return a null pointer upon reaching the end of the directory stream. The structure dirent defined in the <dirent.h> header describes a directory entry. The readdir() function shall not return directory entries containing empty names. If entries for dot or dot-dot exist, one entry shall be returned for dot and one entry shall be returned for dot-dot; otherwise, they shall not be returned. The pointer returned by readdir() points to data which may be overwritten by another call to readdir() on the same directory stream. This data is not overwritten by another call to readdir() on a different directory stream. If a file is removed from or added to the directory after the most recent call to opendir() or rewinddir(), whether a subsequent call to readdir() returns an entry for that file is unspecified. The readdir() function may buffer several directory entries per actual read operation; readdir() shall mark for update the st_atime field of the directory each time the directory is actually read. After a call to fork(), either the parent or child (but not both) may continue processing the directory stream using readdir(), rewinddir(), [XSI] [Option Start]  or seekdir(). [Option End] If both the parent and child processes use these functions, the result is undefined. If the entry names a symbolic link, the value of the d_ino member is unspecified. The readdir() function need not be reentrant. A function that is not required to be reentrant is not required to be thread-safe.

 **Closedir** closedir() function shall close the directory stream referred to by the argument dirp. Upon return, the value of dirp may no longer point to an accessible object of the type DIR. If a file descriptor is used to implement type DIR, that file descriptor shall be closed.

 **Strerror** strerror() function returns a pointer to a string that describes the error code passed in the argument errnum, possibly using the LC_MESSAGES part of the current locale to select the appropriate language.

 **Perror** perror() function displays the description of the error that corresponds to the error code stored in the system variable errno . errno is a system variable that holds the error code referring to the error condition. A call to a library function produces this error condition.

 **Isatty** isatty() is a function that returns 1 if the fd - (file descriptor) refers to a terminal.

 **Ttyname** ttyname() returns a pointer to the null-terminated pathname of the terminal device that is open on the file descriptor fd, or NULL on error (for example, if fd is not connected to a terminal).The return value may point to static data, possibly overwritten by the next call.The function ttyname_r() stores this pathname in the buffer buf of length buflen.

 **Ttyslot** ttyslot() returns the index of the current user's entry in some file. Now "What file?" you ask.  Well, let's first look at some history.

 **Ioctl** ioctl() system call manipulates the underlying device parameters of special files.  In particular, many operating characteristics of character special files (e.g., terminals) may be controlled with ioctl() requests.  The argument fd must be an open file descriptor. The second argument is a device-dependent request code.  The third argument is an untyped pointer to memory.  It's traditionally char *argp (from the days before void * was valid C), and will be so named for this discussion. An ioctl() request has encoded in it whether the argument is an in parameter or out parameter, and the size of the argument argp in bytes.

 **Getenv** searches for the environment string pointed to by name and returns the associated value to the string.

 **Tcsetattr** tcsetattr() function shall set the parameters associated with the terminal referred to by the open file descriptor fildes (an open file descriptor associated with a terminal) from the termios structure referenced by termios_p as follows:
If optional_actions is TCSANOW, the change shall occur immediately. If optional_actions is TCSADRAIN, the change shall occur after all output written to fildes is transmitted. This function should be used when changing parameters that affect output. If optional_actions is TCSAFLUSH, the change shall occur after all output written to fildes is transmitted, and all input so far received but not read shall be discarded before the change is made. If the output baud rate stored in the termios structure pointed to by termios_p is the zero baud rate, B0, the modem control lines shall no longer be asserted. Normally, this shall disconnect the line. If the input baud rate stored in the termios structure pointed to by termios_p is 0, the input baud rate given to the hardware is the same as the output baud rate stored in the termios structure. The tcsetattr() function shall return successfully if it was able to perform any of the requested actions, even if some of the requested actions could not be performed. It shall set all the attributes that the implementation supports as requested and leave all the attributes not supported by the implementation unchanged. If no part of the request can be honored, it shall return -1 and set errno to [EINVAL]. If the input and output baud rates differ and are a combination that is not supported, neither baud rate shall be changed. A subsequent call to tcgetattr() shall return the actual state of the terminal device (reflecting both the changes made and not made in the previous tcsetattr() call). The tcsetattr() function shall not change the values found in the termios structure under any circumstances.

 **Tcgetattr** tcgetattr() function shall get the parameters associated with the terminal referred to by fildes and store them in the termios structure referenced by termios_p. The fildes argument is an open file descriptor associated with a terminal. The termios_p argument is a pointer to a termios structure. The tcgetattr() operation is allowed from any process. If the terminal device supports different input and output baud rates, the baud rates stored in the termios structure returned by tcgetattr() shall reflect the actual baud rates, even if they are equal. If differing baud rates are not supported, the rate returned as the output baud rate shall be the actual baud rate. If the terminal device does not support split baud rates, the input baud rate stored in the termios structure shall be the output rate (as one of the symbolic values).

 **Tgetent** tgetent routine loads the entry for name. It returns 1 on success, 0 if there is no such entry, and -1 if the terminfo database could not be found. The emulation ignores the buffer pointer bp.

 **Tgetflag** tgetflag routine gets the boolean entry for id, or zero if it is not available.

 **Tgetnum** tgetnum routine gets the numeric entry for id, or -1 if it is not available.

 **Tgetstr** tgetstr routine returns the string entry for id, or zero if it is not available. Use tputs to output the returned string. The return value will also be copied to the buffer pointed to by area, and the area value will be updated to point past the null ending this value. Only the first two characters of the id parameter of tgetflag, tgetnum and tgetstr are compared in lookups.

 **Tgoto** tgoto routine instantiates the parameters into the given capability. The output from this routine is to be passed to tputs.

 **Tputs** tputs routine is described on the curs_terminfo(3X) manual page. It can retrieve capabilities by either termcap or terminfo name. The variables PC, UP and BC are set by tgetent to the terminfo entry's data for pad_char, cursor_up and backspace_if_not_bs, respectively. UP is not used by ncurses. PC is used in the tdelay_output function. BC is used in the tgoto emulation. The variable ospeed is set by ncurses in a system-specific coding to reflect the terminal speed.

# minishell Evaluation Sheet (As of November 2022) 

**Mandatory Part**

- [ ] Use "make -n" to see if compilation use "-Wall -Wextra -Werror". If not, select the "invalid compilation" flag.
- [ ]  minishell compiles without any errors. If not, select the flag.
- [ ] The Makefile must not re-link. If not, select the flag.

**Simple Command & global variables**

- [ ] Execute a simple command with an absolute path like /bin/ls, or any other command without any options.
- [ ]  How many global variables are used? Why? Ask the evaluated student to give you a concrete example of why it feels mandatory or logical.
- [ ]  Test an empty command.
- [ ] Test only spaces or tabs.
- [ ]  If something crashes, select the "crash" flag.
- [ ] If something doesn't work, select the "incomplete work" flag.

**Arguments & History**

- [ ]  Execute a simple command with an absolute path like /bin/ls, or any other command with arguments but without any quotes or double quotes.
- [ ] Repeat multiple times with different commands and arguments.
- [ ] If something crashes, select the "crash" flag.
- [ ]  If something doesn't work, select the "incomplete work" flag.

**Echo**
- [ ] Execute the echo command with or without arguments, or the -n option.
- [ ] Repeat multiple times with different arguments.
- [ ]  If something crashes, select the "crash" flag.
- [ ]  If something doesn't work, select the "incomplete work" flag.

**Exit**
- [ ]  Execute exit command with or without arguments.
- [ ]  Repeat multiple times with different arguments.
- [ ]  Don't forget to relaunch the minishell
- [ ] If something crashes, select the "crash" flag.
- [ ]  If something doesn't work, select the "incomplete work" flag.

**Return value of a process**

- [ ]  Execute a simple command with an absolute path like /bin/ls, or any other command with arguments but without any quotes and double quotes.

**Then execute echo $?**

- [ ] Check the printed value. You can do the same in bash in order to compare the results.
- [ ]  Repeat multiple times with different commands and arguments. Try some wrong commands like '/bin/ls filethatdoesntexist'
- [ ]  Try anything like expr $? + $?
- [ ]  If something crashes, select the "crash" flag.
- [ ]  If something doesn't work, select the "incomplete work" flag.

**Signals**
- [ ]  ctrl-C in an empty prompt should display a new line with a new prompt.
- [ ]  ctrl-\ in an empty prompt should not do anything.
- [ ]  ctrl-D in an empty prompt should quit minishell --> RELAUNCH!
- [ ] ctrl-C in a prompt after you wrote some stuff should display a new line with a new prompt.
- [ ]  The buffer should be clean too. Press "Enter" to make sure nothing from the previous line is executed.
- [ ]  ctrl-D in a prompt after you wrote some stuff should not do anything.
- [ ]  ctrl-\ in a prompt after you wrote some stuff should not do anything.
- [ ]  Try ctrl-C after running a blocking command like cat without arguments or grep "something".
- [ ]  Try ctrl-\ after running a blocking command like cat without arguments or grep "something".
- [ ]  Try ctrl-D after running a blocking command like cat without arguments or grep "something".
- [ ]  Repeat multiple times using different commands.
- [ ]  If something crashes, select the "crash" flag.
- [ ]  If something doesn't work, select the "incomplete work" flag.

**Double Quotes**

- [ ]  Execute a simple command with arguments and, this time, use also double quotes (you should try to include whitespaces too).
- [ ]  Try a command like : echo "cat lol.c | cat > lol.c"
- [ ] Try anything except $.
- [ ]  If something crashes, select the "crash" flag.
- [ ]  If something doesn't work, select the "incomplete work" flag.

**Single Quotes**

- [ ]  Execute commands with single quotes as arguments.
- [ ] Try empty arguments.
- [ ] Try environment variables, whitespaces, pipes, redirection in the single quotes.
- [ ]  echo '$USER' must print $USER.
- [ ]  Nothing should be interpreted.

**env**

- [ ]  Check if env shows you the current environment variables.

**export**

- [ ]  Export environment variables, create new ones and replace old ones.
- [ ] Check the result with env.

**unset**
- [ ]  Export environment variables, create new ones and replace old ones.
- [ ]  Use unset to remove some of them.
- [ ]  Check the result with env. 

**cd**

- [ ] Use the command cd to move the working directory and check if you are in the right directory with /bin/ls
- [ ]  Repeat multiple times with working and not working cd
- [ ]  Also, try '.' and '..' as arguments.

**Pwd**

- [ ]  Use the command pwd.
- [ ] Repeat multiple times in different directories.

**Relative Path**

- [ ]  Execute commands but this time use a relative path.
- [ ]  Repeat multiple times in different directories with a complex
relative path (lots of ..).

**Environment path**

- [ ] Execute commands but this time without any path (ls, wc, awk and so forth).
- [ ]  Unset the $PATH and ensure commands are not working anymore.
- [ ] Set the $PATH to a multiple directory value (directory1:directory2) and ensure that directories are checked in order from left to right.

**Redirection**

- [ ] Execute commands with redirections < and/or >
- [ ]  Repeat multiple times with different commands and arguments and sometimes change > with >>
- [ ]  Check if multiple tries of the same redirections fail.
- [ ]  Test << redirection (it doesn't have to update the history).

**Pipes**

- [ ]  Execute commands with pipes like 'cat file | grep bla | more'
- [ ] Repeat multiple times with different commands and arguments.
- [ ]  Try some wrong commands like 'ls filethatdoesntexist | grep bla | more'
- [ ]  Try to mix pipes and redirections.

**Go Crazy and history**

- [ ]  Type a command line, then use ctrl-C and press "Enter". The buffer should be clean and there should be nothing left to execute.
- [ ]  Can we navigate through history using Up and Down? Can we retry some command?
- [ ] Execute commands that should not work like 'dsbksdgbksdghsd'.

**Ensure minishell doesn't crash and prints an error.**

- [ ] 'cat | cat | ls' should behave in a "normal way".
- [ ] Try to execute a long command with a ton of arguments.
- [ ]  Have fun with that beautiful minishell and enjoy it!

**Environment variables**

- [ ] Execute echo with some environment variables ($variable) as arguments.
- [ ]  Check that $ is interpreted as an environment variable.
- [ ] Check that double quotes interpolate $.
- [ ] Check that USER exists. Otherwise, set it.
- [ ] echo "$USER" should print the value of the USER variable.

**Bonus**

*Evaluate the bonus part if, and only if, the mandatory part has been entirely and perfectly done, and the error management handles unexpected or bad usage. In case all the mandatory points were not passed during the defense, bonus points must be totally ignored.*

**And, Or**
- Use &&, || and parenthesis with commands and ensure minishell behaves
the same way bash does.

**Wildcard**

- Use wildcards in arguments in the current working directory.

**Surprise! (or not...)**

- Set the USER environment variable.
- echo "'$USER'" should print the value of the USER variable.
- echo '"$USER"' should print "$USER".
