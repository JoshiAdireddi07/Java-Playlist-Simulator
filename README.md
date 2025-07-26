# Java-Playlist-Simulator
//Java project idea — simple, interactive, and demonstrates solid OOP and logic concepts.

    import java.util.*;

    class Song {
    String title;
    String artist;
    int duration; // in seconds

    Song(String title, String artist, int duration) {
        this.title = title;
        this.artist = artist;
        this.duration = duration;
    }

    void play() {
        System.out.println("🎵 Now Playing: " + title + " by " + artist + " (" + duration + " sec)");
    }
    }

    public class PlaylistSimulator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Song> playlist = new ArrayList<>();

        // Default songs
        playlist.add(new Song("Lofi Dreams", "SynthCat", 145));
        playlist.add(new Song("Heaven Knows", "The Smiths", 216));
        playlist.add(new Song("Chill Vibes", "Lo Beat", 122));

        while (true) {
            System.out.println("\n🎧 Music Playlist Menu:");
            System.out.println("1. View Playlist");
            System.out.println("2. Play a Song");
            System.out.println("3. Add New Song");
            System.out.println("4. Shuffle Playlist");
            System.out.println("5. Exit");
            System.out.print("Choose an option: ");
            int choice = sc.nextInt();
            sc.nextLine(); // consume newline

            switch (choice) {
                case 1:
                    System.out.println("\nYour Playlist:");
                    for (int i = 0; i < playlist.size(); i++) {
                        Song s = playlist.get(i);
                        System.out.println((i + 1) + ". " + s.title + " by " + s.artist);
                    }
                    break;

                case 2:
                    System.out.print("Enter song number to play: ");
                    int index = sc.nextInt() - 1;
                    if (index >= 0 && index < playlist.size()) {
                        playlist.get(index).play();
                    } else {
                        System.out.println("❌ Invalid choice!");
                    }
                    break;

                case 3:
                    System.out.print("Enter title: ");
                    String title = sc.nextLine();
                    System.out.print("Enter artist: ");
                    String artist = sc.nextLine();
                    System.out.print("Enter duration (sec): ");
                    int duration = sc.nextInt();
                    playlist.add(new Song(title, artist, duration));
                    System.out.println("✅ Song added!");
                    break;

                case 4:
                    Collections.shuffle(playlist);
                    System.out.println("🔀 Playlist shuffled!");
                    break;

                case 5:
                    System.out.println("👋 Exiting. Keep vibing!");
                    return;

                default:
                    System.out.println("❌ Invalid input. Try again.");
            }
        }
    }
}
