cliffhanger4753
cliffhanger4753
En ligne

Turo — 17/04/2025 13:22
kqjer
qjwer
qkwejr
_errorCodes["401"] = "No such nick/channel";
    _errorCodes["403"] = "No such channel";
    _errorCodes["421"] = "Unknown command";
    _errorCodes["431"] = "No nickname given";
    _errorCodes["432"] = "Erroneous nickname";
    _errorCodes["433"] = "Nickname is already in use";
    _errorCodes["441"] = "They aren't on that channel";
    _errorCodes["442"] = "You're not on that channel";
    _errorCodes["461"] = "Not enough parameters";
    _errorCodes["472"] = "Unknown mode char";
    _errorCodes["473"] = "Cannot join channel (+i)";
    _errorCodes["474"] = "Cannot join channel (+b)";
    _errorCodes["475"] = "Cannot join channel (+k)";
    _errorCodes["476"] = "Bad channel mask";
    _errorCodes["481"] = "Permission Denied (You're not an IRC operator)";
    _errorCodes["482"] = "You're not channel operator";
    _errorCodes["484"] = "Your connection is restricted";
    _errorCodes["491"] = "No O-lines for your host";
    _errorCodes["501"] = "Unknown MODE flag";
    _errorCodes["502"] = "Cannot change mode for other users";
Turo — 17/04/2025 13:57
https://modern.ircdocs.horse/#errneedmoreparams-461
Turo — 22/04/2025 10:24
Commandes essentielles à implémenter
NICK
Cette commande définit le pseudonyme du client. Vous devez:

Vérifier si le pseudo est déjà utilisé
Enregistrer le nouveau pseudo pour ce client
Répondre avec un message de confirmation ou d'erreur
Réponse en cas de succès:
":servername 001 nickname :Welcome to the IRC Network nickname"

Réponse en cas d'erreur (pseudo déjà utilisé):
":servername 433 * nickname :Nickname is already in use"
USER
Cette commande fournit le nom d'utilisateur et le nom réel. Elle est généralement envoyée avec NICK lors de la connexion:
Réponse en cas de succès (plusieurs messages):
":servername 001 nickname :Welcome to the IRC Network"
":servername 002 nickname :Your host is servername, running version 1.0"
":servername 003 nickname :This server was created..."
":servername 004 nickname :servername 1.0 o o"
JOIN
Permet à un utilisateur de rejoindre un canal. Vous devez:

Vérifier si le canal existe (le créer sinon)
Vérifier les restrictions (mot de passe, invitation, limite d'utilisateurs)
Ajouter l'utilisateur au canal
Informer tous les membres du canal qu'un nouvel utilisateur a rejoint
Réponse en cas de succès:
":nickname!username@host JOIN :#channel"
":servername 353 nickname = #channel :nickname1 nickname2 ..." (liste des utilisateurs)
":servername 366 nickname #channel :End of /NAMES list"

Réponse en cas d'erreur (canal sur invitation uniquement):
":servername 473 nickname #channel :Cannot join channel (+i)"
PRIVMSG
Permet d'envoyer des messages privés à un utilisateur ou un canal:
Pour un message dans un canal:
":nickname!username@host PRIVMSG #channel :message"
(Transmis à tous les membres du canal)

Pour un message privé:
":nickname!username@host PRIVMSG recipient :message"
(Transmis uniquement au destinataire)
PING/PONG
Mécanisme pour vérifier si la connexion est active:
Quand le client envoie PING:
"PONG :argument" (retournez l'argument fourni)
Commandes pour opérateurs
KICK
Permet à un opérateur de canal d'éjecter un utilisateur:
Réponse à tous les membres du canal:
":nickname!username@host KICK #channel target :raison"
INVITE
Permet d'inviter un utilisateur à rejoindre un canal:
Réponse à l'expéditeur:
":servername 341 nickname target #channel"

Réponse à la cible:
":nickname!username@host INVITE target :#channel"
TOPIC
Change ou affiche le sujet d'un canal:
Pour définir un sujet:
":nickname!username@host TOPIC #channel :nouveau sujet"
(Transmis à tous les membres du canal)

Pour afficher le sujet actuel:
":servername 332 nickname #channel :sujet actuel"
":servername 333 nickname #channel nickname!username@host timestamp"
MODE
Change les modes d'un canal ou d'un utilisateur. Pour les modes de canal mentionnés:
Pour changer un mode:
":nickname!username@host MODE #channel +/-flags arguments"

Exemples:
"+i" (canal sur invitation uniquement)
"+t" (seuls les opérateurs peuvent changer le sujet)
"+k mot_de_passe" (définir un mot de passe)
"+o nickname" (donner le statut d'opérateur)
"+l nombre" (définir une limite d'utilisateurs)
Structure des réponses IRC
Les réponses IRC suivent généralement cette structure:
":source COMMANDE destination :message"
:source est l'origine du message (serveur ou utilisateur)
COMMANDE est la commande ou le code numérique
destination est le destinataire (utilisateur ou canal)
:message est le contenu du message
Turo — 30/04/2025 13:02
ssize_t sent = send(client_fd, response.c_str(), response.length(), 0);
    if (sent < 0)
        throw std::runtime_error(std::string("send: ") + std::strerror(errno));
cliffhanger4753 — 07/05/2025 09:59
#!/bin/bash

HOST=localhost
PORT=4808

# Terminal 1 : alice
Afficher plus
init.sh
3 Ko
cliffhanger4753 — 14/05/2025 13:21
Type de fichier joint : acrobat
Tableau de Tests pour la Commande MODE.pdf
419.56 KB
Turo — 15/05/2025 14:31
signal(SIGPIPE, handleSignal);
signal(SIGPIPE, handleSignal);
Turo — 15/05/2025 15:26
:nickname!~username@hostname MODE #chan +o nicknameTarget
:Sophie42!~sophie@78.45.231.19 MODE #programmation +o Jean_Dev
Turo — 20/05/2025 12:51
Type de fichier joint : acrobat
ng_5_ft_irc.pdf
171.55 KB
cliffhanger4753 — 20/05/2025 15:50
mkdir -p ~/.irssi2
cp ~/.irssi/config ~/.irssi2/
nano ~/.irssi2/config
(modifiez les valeurs de "user_name" et "nick")
Lancez la seconde instance d'irssi avec cette configuration:
irssi --home=~/.irssi2
Turo — 09/07/2025 13:59
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
d02 ,omik6nu556b`1
Turo — 10:15
# <p align="center"> Hello, welcome to my GitHub! <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"></p> 

<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&pause=1000&color=F7F7F7&center=true&vCenter=true&width=435&lines=Tech+Enthusiast;Continuous+Learner" alt="Typing SVG" />
</div>
</br>
Afficher plus
message.txt
4 Ko
﻿
Turo
turothereal
# <p align="center"> Hello, welcome to my GitHub! <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"></p> 

<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&pause=1000&color=F7F7F7&center=true&vCenter=true&width=435&lines=Tech+Enthusiast;Continuous+Learner" alt="Typing SVG" />
</div>
</br>
<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

## <img src="https://github.com/7oSkaaa/7oSkaaa/raw/main/Images/about_me.gif?raw=true" width="30"> About Me
</br>

<div align="center">
  <img align="right" alt="Coding" width="250" src="https://github.com/7oSkaaa/7oSkaaa/blob/main/Images/Software_Tools.gif">
  
  <p align="left" style="margin-left: 20px; line-height: 1.6;">
    • 🌱 Leaner at 42 Paris.</br>
    • 🔭 <a href="https://arthur-portfolio.com/?utm_source=github&utm_medium=repository&utm_campaign=portfolio&utm_content=readme_link">Discover my portfolio</a></br>
    • ⚡ Fun fact: I like durian.</br></br>
    Feel free to reach me out.</br>
    • 📧 <a href="mailto:your.email@gmail.com">By Email</a></br>
    • 👔 <a href="https://www.linkedin.com/in/arthurbernard92/">Via LinkedIn</a></br>
  </p>
</div>
</br>

## <img src="https://media2.giphy.com/media/QssGEmpkyEOhBCb7e1/giphy.gif?cid=ecf05e47a0n3gi1bfqntqmob8g9aid1oyj2wr3ds3mg700bl&rid=giphy.gif" width="25"> Skills & Technologies
</br>

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg" height="50" width="50" alt="c logo" />
 <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg" height="50" width="50" alt="cpp logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="50" width="50" alt="html5 logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="50" width="50" alt="css3 logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" height="50" width="50" alt="docker logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" height="50" width="50" alt="github logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" height="50" width="50" alt="git logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" height="50" width="50" alt="figma logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="50" width="50" alt="javascript logo" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="50" width="50" alt="python logo" />
  
</div>
</br>

## <img src="https://media.giphy.com/media/iY8CRBdQXODJSCERIr/giphy.gif" width="30"> My Projects
</br>

<div align="center">
  <a href="https://github.com/TuroTheReal/minishell">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=TuroTheReal&repo=minishell&theme=radical" alt="minishell" />
  </a>
  <a href="https://github.com/TuroTheReal/inception">
    <img src="https://github-readme-stats.vercel.app/api/pin/?username=TuroTheReal&repo=inception&theme=radical" alt="inception" />
  </a>
</div>
</br>

## <img src="https://media.giphy.com/media/cj87CxfRtrUifF3Ryk/giphy.gif" width="30"> GitHub Stats
</br>

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=TuroTheReal&theme=radical" alt="Top Languages"/>
</div>
message.txt
4 Ko