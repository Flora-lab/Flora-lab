java
import java.util.Scanner;

class Compte {
    private double solde;

    public Compte(double solde) {
        this.solde = solde;
    }

    public double getSolde() {
        return solde;
    }

    public void setSolde(double nouveauSolde) {
        solde = nouveauSolde;
    }
}

class CompteEpargne extends Compte {
    private double taux;

    public CompteEpargne(double solde, double taux) {
        super(solde);
        this.taux = taux;
    }

    public double calculInterets() {
        return taux * getSolde();
    }
}

class ComptePrivé extends Compte {
    private double taux;

    public ComptePrivé(double solde, double taux) {
        super(solde);
        this.taux = taux;
    }

    public double calculInterets() {
        return taux * getSolde();
    }
}

class Affichage {
    public static void afficherClient(String nom, String ville, double solde) {
        System.out.println("Client " + nom + " de " + ville + " : " + solde + " francs");
    }

    public static void afficherClient(String nom, String ville, double solde1, double solde2) {
        System.out.println("Client " + nom + " de " + ville + " :");
        System.out.println("  Compte privé : " + solde1 + " francs");
        System.out.println("  Compte d'épargne : " + solde2 + " francs");
    }
}

public class Exercice2 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Données avant le bouclage des comptes:");
        System.out.println("Client Pedro de Geneve");
        System.out.println("Compte privé : 1000.0 francs");
        System.out.println("Compte d'épargne : 2000.0 francs");
        System.out.println("Client Alexandra de Lausanne");
        System.out.println("Compte privé : 3000.0 francs");
        System.out.println("Compte d'épargne : 4000.0 francs");

        ComptePrivé comptePedro = new ComptePrivé(1000, 0.01);
        CompteEpargne comptePedroEpargne = new CompteEpargne(2000, 0.005);

        ComptePrivé compteAlexandra = new ComptePrivé(3000, 0.02);
        CompteEpargne compteAlexandraEpargne = new CompteEpargne(4000, 0.01);

        Affichage.afficherClient("Pedro", "Geneve", comptePedro.getSolde(), comptePedroEpargne.getSolde());
        Affichage.afficherClient("Alexandra", "Lausanne", compteAlexandra.getSolde(), compteAlexandraEpargne.getSolde());

        double interetsPedro = comptePedro.calculInterets();
        double interetsPedroEpargne = comptePedroEpargne.calculInterets();
        double interetsAlexandra = compteAlexandra.calculInterets();
        double interetsAlexandraEpargne = compteAlexandraEpargne.calculInterets();

        System.out.println("Données après le bouclage des comptes:");
        System.out.println("Client Pedro de Geneve");
        System.out.println("Compte privé : " + (comptePedro.getSolde() + interetsPedro) + " francs");
        System.out.println("Compte d'épargne : " + (comptePedroEpargne.getSolde() + interetsPedroEpargne) + " francs");
        System.out.println("Client Alexandra de Lausanne");
        System.out.println("Compte privé : " + (compteAlexandra.getSolde() + interetsAlexandra) + " francs");
        System.out.println("Compte d'épargne : " + (compteAlexandraEpargne.getSolde() + interetsAlexandraEpargne) + " francs");

        scanner.close();
    }
}
