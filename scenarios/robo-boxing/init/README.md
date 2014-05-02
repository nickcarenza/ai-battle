Robo+Boxing
===========
Duck, juke, hook and jab. Your AI can respond to events like `incomingLeftJab` and respond with punches like `jukeRight()`, but beware the `fakeLeftJeb()` and `rightUppoercut()` combo!.

Event API
---------
 - all
 - Incoming
     + incomingLeftJab
     + incomingRightJab
     + incomingLeftUppercut
     + incomingRightUppercut
     + incomingLeftHook
     + incomingRightHook
     + incomingLeftHaymaker
     + incomingRightHaymaker
 - Hit by
     + hitByLeftJab
     + hitByRightJab
     + hitByLeftUppercut
     + hitByRightUppercut
     + hitByLeftHook
     + hitByRightHook
     + hitByLeftHaymaker
     + hitByRightHaymaker
 - Connected with
     + connectedWithLeftJab
     + connectedWithRightJab
     + connectedWithLeftUppercut
     + connectedWithRightUppercut
     + connectedWithLeftHook
     + connectedWithRightHook
     + connectedWithLeftHaymaker
     + connectedWithRightHaymaker
 - Status
     + selfDazeStart
     + selfDazeEnd
     + opponentDazeStart
     + opponentDazeEnd
 - Evasion
     + selfBlocked
     + selfDodged
     + selfJuked
     + opponentBlocked
     + opponentDodged
     + opponentJuked

Boxing API
----------
Each method takes 2 arguments, a success callback and a failure callback
 - Jukes
     + juke( LEFT | RIGHT )
 - Dodges
     + dodge( LEFT | RIGHT )
 - Jabs
     + leftJab()
     + rightJab()
 - Hooks
     + leftHook()
     + rightHook()
 - Uppercuts
     + leftUppercut()
     + rightUppercut()
 - Haymakers
     + leftHaymaker()
     + rightHaymaker()
 - Fakes
     + fakeLeftJab()
     + fakeRightJab()
     + fakeLeftHook()
     + fakeRightHook()
     + fakeLeftUppercut()
     + fakeRightUppercut()
     + fakeLeftHaymaker()
     + fakeRightHaymaker()
 - Blocks
     + blockHighLeft()
     + blockHighMiddle()
     + blockHighRIght()
     + blockLowLeft()
     + blockLowMiddle()
     + blockLowRight()
 - Leans
     + leanLeft()
     + leanRight()
     + leanBack()

Example 1
---------
    Event.listen('incomingLeftJab', counterRight);

    function counterRight(event) {
        Boxing.leanRight(jabRight);
    }

Memory API
----------
 - lastEvent
 - nextEvent

Example 2
---------
    Event.all(function(event){
        if(/hitBy/.test(e.name)) {
            safetyMode(event);
        }
    });

    function safetyMode(event) {
        Event.all(function(event) {
            if(/incoming/.test(e.name)) {
                block(e.vertical, e.horizontal);
                lean(~e.horizontal);
            }
        });
    }