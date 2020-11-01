# Czaszki
# Oficjalny ,autorski skrypt działający na moim serwerze (Arkanowice).
on death:
    if victim and attacker is a player:
        if {skull::%victim%} is 0:
            set {skull::%attacker%} to 1
            add player to {skulls}
            execute console command "/eco take %attacker% 50"
            send "&cGracz %attacker% zamordowal pokojowego gracza %victim%. Kara -hunt i -50$" to all players 
        if {skull::%victim%} is 1:
            set {skull::%victim%} to 0 
            execute console command "/eco give %attacker% 100"
            send "&eGracz %attacker% zabil grozniego gracza %victim%. Otrzymuje nagrode 100!" to all players 

command /hunceni:
	trigger:
		send "&0[&6A&0] &7Gracze &4hunceni &7na naszym serwerze! &e%{skull::*}%&7." to player 
		
command /nalozhunt [<offlineplayer>]:
	trigger:
		if player has permission "arskulls.skullon":	
			set {skull::%arg 1%} to 1
			send "&0[&6A&0] &7Nalozono &4hunt &7na garcza &8%arg 1%&7!." to all players 
		else:
			send "&0[&6A&0] &4NMie masz permisji do tej komendy!" to player 

command /zdejmijhunt [<offlineplayer>]:
	trigger:
		if player has permission "arskulls.skullof":	
			set {skull::%arg 1%} to 0
			send "&0[&6A&0] &7Gracz &8%arg 1% &7zostal &eoczyszczony&7. Od teraz nie ma hunta!" to all players 
		else:			
			send "&0[&6A&0] &4Nie masz permisji to tej komendy!" to player 

		

		
