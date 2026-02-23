<?php
/*********************************************************************
* Author: Soulaiman Ayhoun
* Date: 11-2-26
* Description: Game - alleen winst bij openen schatkist, einde toont resultaat
*********************************************************************/

// ASCII prijs die wordt getoond bij winst
$prize =  "      _______\n" .
          "     |$$$$$$$|\n" .
          "     |$$$$$$$|\n" .
          "     |$$$$$$$|\n" .
          "     '-------'\n";

// Variabele om opnieuw spelen mogelijk te maken
$playAgain = "ja";

// === WHILE LOOP START ===
while ($playAgain == "ja") {

    $hasKey = false;
    $won = false; // Bijhouden of speler gewonnen heeft

    // Introductie
    printf("\nWelkom bij het avontuur van de verborgen schat!\n\n");

    // ASCII boom
    printf("       /\\\n");
    printf("      /  \\\n");
    printf("     /++++\\\n");
    printf("    /  ()  \\\n");
    printf("   /        \\\n");
    printf("   ----------\n\n");

    // =========================
    // EERSTE KEUZE
    // =========================
    printf("Je staat aan de rand van een mystiek bos. Twee paden liggen voor je:\n");
    printf("Optie 1: Een smal pad bedekt met glinsterende stenen\n");
    printf("Optie 2: Een breed pad dat naar een mistige heuvel leidt\n");
    printf("Maak je keuze 1 of 2:\n");

    $userChoice = readline("");

    /*  Pad 1 */
    if ($userChoice == 1) {

        printf("\nJe volgt het smalle pad en komt bij een rivier.\n");
        printf("Optie 1: Steek de rivier over\n");
        printf("Optie 2: Volg de rivier stroomafwaarts\n");

        $userChoice = readline("");

        if ($userChoice == 1) {

            printf("\nAan de overkant zie je een grot.\n");
            printf("In de grot ligt iets glinsterends op de grond.\n");
            printf("Optie 1: Pak het op\n");
            printf("Optie 2: Negeer het en loop verder\n");

            $userChoice = readline("");

            if ($userChoice == 1) {
                printf("\nJe hebt een gouden sleutel gevonden! 🗝️\n");
                $hasKey = true;
            } else {
                printf("\nJe laat het glinsterende voorwerp liggen…\n");
            }

            // ===== MINI BOSS FIGHT (Goblin) =====
            printf("\nOpeens verschijnt er een goblin! 🧌\n");
            printf("Optie 1: Vecht tegen de goblin\n");
            printf("Optie 2: Vlucht terug naar de rivier\n");

            $fightChoice = readline("");

            if ($fightChoice == 1) {
                printf("Je vecht dapper en overwint de goblin! 🏆\n");
            } elseif ($fightChoice == 2) {
                printf("\nJe vlucht terug en raakt verdwaald… 🌲\n");
                $playAgain = readline("\nWil je opnieuw spelen? (ja/nee): ");
                continue;
            } else {
                printf("\nOngeldige keuze! Een goblin lacht je uit 😅\n");
                $playAgain = readline("\nWil je opnieuw spelen? (ja/nee): ");
                continue;
            }

            // ===== KEUZES NA SLEUTEL & MINI BOSS (PAD 1) =====
            printf("\nWat doe je nu?\n");
            printf("Optie 1: Open de schatkist (als je de sleutel hebt)\n");
            printf("Optie 2: Zoek een geheime gang in de grot\n");

            $keyChoice = readline("");

            if ($keyChoice == 1 && $hasKey) {
                printf("🎉 Fantastisch! Je opent de schatkist vol goud en juwelen! 💰\n\n");
                printf("%s", $prize);
                $won = true;
            } elseif ($keyChoice == 2) {
                printf("\nJe ontdekt een geheime gang.\n");
                printf("Aan het einde zie je een mysterieus altaar.\n");
                printf("Optie 1: Leg de sleutel op het altaar\n");
                printf("Optie 2: Bewaar de sleutel\n");

                $secretChoice = readline("");

                if ($secretChoice == 1 && $hasKey) {
                    printf("\n✨ Het altaar opent een verborgen schatkamer! Je hebt gewonnen! 🎊\n\n");
                    printf("%s", $prize);
                    $won = true;
                } else {
                    printf("\nHet altaar reageert niet… maar het avontuur blijft spannend! 🌌\n");
                }
            }

        } else {
            // PAD 1 alternatief: bootwrak
            printf("\nJe volgt de rivier en komt bij een oud wrak van een boot.\n");
            printf("Optie 1: Onderzoek het wrak\n");
            printf("Optie 2: Loop verder het bos in\n");

            $userChoice = readline("");

            if ($userChoice == 1) {
                printf("\nJe vindt een verborgen sleutel tussen de planken! 🗝️\n");
                $hasKey = true;

                // Extra keuzes na vinden sleutel
                printf("\nWat doe je nu?\n");
                printf("Optie 1: Vecht tegen een goblin\n");
                printf("Optie 2: Zoek de schatkist in de grot\n");

                $extraChoice = readline("");
                if ($extraChoice == 1) {
                    printf("Je overwint de goblin! 🏆\n");
                } else {
                    printf("\nJe gaat naar de schatkist...\n");
                    printf("🎉 Je opent de schatkist! 💰\n%s", $prize);
                    $won = true;
                }
            } else {
                printf("\nJe loopt verder, maar de schat blijft onbereikbaar… 😅\n");
            }
        }
    }

    /* 
       PAD 2 (RUÏNE)
    */
    elseif ($userChoice == 2) {
        printf("\nJe volgt het brede pad naar de mistige heuvel…\n");
        printf("Bovenaan zie je een ruïne en een donkere gang.\n");
        printf("Optie 1: Onderzoek de ruïne\n");
        printf("Optie 2: Ga de donkere gang in\n");

        $userChoice = readline("");

        if ($userChoice == 1) {
            printf("\nIn de ruïne zie je een oude tafel met een klein kistje.\n");
            printf("Optie 1: Open het kistje\n");
            printf("Optie 2: Loop verder\n");

            $userChoice = readline("");

            if ($userChoice == 1) {
                printf("\nJe vindt een mysterieuze sleutel! 🗝️\n");
                $hasKey = true;
            } else {
                printf("\nJe loopt verder zonder iets mee te nemen…\n");
            }

            printf("\nEen stenen golem blokkeert je pad! 🗿\n");
            printf("Optie 1: Vecht tegen de golem\n");
            printf("Optie 2: Probeer te sluipen\n");

            $fightChoice = readline("");

            if ($fightChoice == 1) {
                printf("Je overwint de golem en gaat verder! 🏰\n");
            } elseif ($fightChoice == 2) {
                printf("\nDe golem pakt je! 😱\n");
                $playAgain = readline("\nWil je opnieuw spelen? (ja/nee): ");
                continue;
            }

            // KEUZES NA SLEUTEL & MINI BOSS
            printf("\nWat doe je nu?\n");
            printf("Optie 1: Open de grote schatkist\n");
            printf("Optie 2: Zoek een verborgen kamer\n");

            $keyChoice = readline("");

            if ($keyChoice == 1 && $hasKey) {
                printf("🎉 Geweldig! Je opent de schatkist! 💎\n%s", $prize);
                $won = true;
            } elseif ($keyChoice == 2) {
                printf("\nJe vindt een verborgen trap naar beneden.\n");
                printf("Beneden zie je twee deuren.\n");
                printf("Optie 1: De stenen deur\n");
                printf("Optie 2: De deur met symbolen\n");

                $secretChoice = readline("");

                if ($secretChoice == 2) {
                    printf("\nDe symbolen lichten op en de deur opent een geheime schatkamer! 🌟\n%s", $prize);
                    $won = true;
                } else {
                    printf("\nDe stenen deur blokkeert je, maar het avontuur was leuk! 🏞️\n");
                }
            }
        } elseif ($userChoice == 2) {
            printf("\nDe donkere gang stort in… gelukkig is er nog het bos om te verkennen! 🌲\n");
        }
    } else {
        printf("Ongeldige keuze! Het bos is mysterieus 🌌\n");
    }

    // ===== Einde van het spel - toon resultaat =====
    if ($won) {
        printf("\n🏆 Je hebt gewonnen! Je vond de schat! 💰\n");
    } else {
        printf("\n😢 Je hebt verloren. Je hebt de schatkist niet geopend.\n");
    }

    $playAgain = readline("\nWil je opnieuw spelen? (ja/nee): ");
}

printf("\nBedankt voor het spelen! 👋\n");
