# VS2022-Preview4.1-Bugged
StackOverflowException after update vs2022 preview 4.1

![image](https://i.imgur.com/9wZvOZp.png)

`builder.Services.AddSingleton<IConfiguration>(builder.Configuration);`
[this line](https://github.com/died/VS2022-Preview4.1-Bugged/blob/d4728eafb92f072ebb193537a97bc6f302c5e21f/VS2022%20Preview4.1%20Bugged/Program.cs#L5) will cause StackOverflowException

on VS2022 preview 3.1 it worked, not sure why, but since .NET Framework already called the line by itself, the old version DI code is unnecessary.

And **remove this line can solve the StackOverflowException**
