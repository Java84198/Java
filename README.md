//Giuseppe Amoddio Licence for this software

package risiko.risiko;

/**
 *
 * @author giuseppeamoddio
 */
import java.util.ArrayList;
import java.util.List;
import java.util.Random;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        List<Territorio> territori = new ArrayList<>();
        territori.add(new Territorio("Stati Uniti", 100));
        territori.add(new Territorio("Cina", 200));
        territori.add(new Territorio("Russia", 150));
        territori.add(new Territorio("India", 120));
        territori.add(new Territorio("Brasile", 80));
        territori.add(new Territorio("Australia", 60));
        territori.add(new Territorio("Canada", 50));
        territori.add(new Territorio("Germania", 40));
        territori.add(new Territorio("Francia", 30));
        territori.add(new Territorio("Regno Unito", 20));

        Scanner scanner = new Scanner(System.in);
        System.out.println("Scegli il tuo territorio:");
        for (int i = 0; i < territori.size(); i++) {
            System.out.println((i + 1) + ". " + territori.get(i).getNome() + " - " + territori.get(i).getTruppe() + " truppe");
        }
        int scelta = scanner.nextInt();
        Territorio territorioGiocatore = territori.get(scelta - 1);
        System.out.println("Hai scelto " + territorioGiocatore.getNome() + ".");

        System.out.println("Scegli un territorio da attaccare:");
        for (int i = 0; i < territori.size(); i++) {
            if (i != scelta - 1) {
                System.out.println((i + 1) + ". " + territori.get(i).getNome() + " - " + territori.get(i).getTruppe() + " truppe");
            }
        }
        int scelta2 = scanner.nextInt();
        Territorio territorioSelezionato = territori.get(scelta2 - 1);
        System.out.println("Hai scelto di attaccare " + territorioSelezionato.getNome() + ".");

        combattimento(territorioGiocatore, territorioSelezionato);
    }

    private static void combattimento(Territorio territorioGiocatore, Territorio territorioSelezionato) {
        Random random = new Random();
        int truppeGiocatore = territorioGiocatore.getTruppe();
        int truppeSelezionato = territorioSelezionato.getTruppe();
        int turno = 0;

        while (truppeGiocatore > 0 && truppeSelezionato > 0 && turno < 6) {
            int dadoGiocatore = random.nextInt(6) + 1;
            int dadoSelezionato = random.nextInt(6) + 1;

            if (dadoGiocatore > dadoSelezionato) {
                truppeSelezionato--;
            } else if (dadoSelezionato > dadoGiocatore) {
                truppeGiocatore--;
            }

            turno++;
        }

        if (truppeGiocatore > 0) {
            territorioSelezionato.setTruppe(0);
            territorioGiocatore.setTruppe(truppeGiocatore + truppeSelezionato);
            System.out.println("Il territorio " + territorioGiocatore.getNome() + " ha vinto il combattimento.");
        } else if (truppeSelezionato > 0) {
            territorioGiocatore.setTruppe(0);
            territorioSelezionato.setTruppe(truppeSelezionato + truppeGiocatore);
            System.out.println("Il territorio " + territorioSelezionato.getNome() + " ha vinto il combattimento.");
        } else {
            System.out.println("Nessun territorio ha vinto il combattimento.");
        }
    }

    static class Territorio {
        private String nome;
        private int truppe;

        public Territorio(String nome, int truppe) {
            this.nome = nome;
            this.truppe = truppe;
        }

        public String getNome() {
            return nome;
        }

        public int getTruppe() {
            return truppe;
        }

        public void setTruppe(int truppe) {
            this.truppe = truppe;
        }
    }
}
