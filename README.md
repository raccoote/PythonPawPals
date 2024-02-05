Link to page: http://pazodimi.webpages.auth.gr/3902partB/

![image](https://github.com/raccoote/Educational-Website/assets/74006924/7a6081fd-2628-421a-a6f4-fd3ae9399c7c)


**Εισαγωγή**

Η ιστοσελίδα "PythonPawPals" πρόκειται για έναν δυναμικό ιστόχωρο που προσφέρει πληροφορίες, πόρους και εργαλεία για την εκμάθηση και την εξάσκηση στη γλώσσα προγραμματισμού Python. Η διάρθρωση κάθε σελίδας αποτελείται από τον header με τον τίτλο, τα περιεχόμενα της σελίδας και από τις πέντε βασικές ενότητες πλοήγησης στα αριστερά, όπως παρουσιάστηκαν και στο α’ μέρος της εργασίας. Ο ιστότοπος μας επιτρέπει την είσοδο login-in ως καθηγητής Tutor με επιπλέον priviliges όπως ανάρτηση/επεξεργασία/διαγραφή ανακοινώσεων, εργασιών και εγγράφων.


**Σύνδεση ως μαθητής και καθηγητής**

Στο μενού πλοήγησης στα αριστερά προστέθηκε η ενότητα ‘Αποσύνδεση’, που οδηγεί στο login page. Μόλις συμπληρωθούνε τα πεδία username και password και πατηθεί το κουμπί ‘Σύνδεση’, ο login.php κώδικας λαμβάνει τα στοιχεία χρήστη από την HTML φόρμα. Εκτελείται ένα ερώτημα SQL για την ανάκτηση των χρηστών με βάση τα δοσμένα στοιχεία. Έπειτα, ελέγχει αν υπάρχει μόνο ένας χρήστης που ταιριάζει. Σε περίπτωση επιτυχίας, αποθηκεύει τον ρόλο του χρήστη σε μια συνεδρία και καθοδηγεί τον χρήστη στην "index.html". Σε διαφορετική περίπτωση, καθοδηγεί τον χρήστη ξανά στη σελίδα σύνδεσης ("login.html").
Παρακάτω παραθέτω μερικά credentials ώστε να συνδεθείτε και με δικαιωματα Tutor, που πέρα απο την προκαθορισμένη εμπειρία που προσφέρει η ιστοσελίδα, επιτρέπεται και η ανάρτηση/επεξεργασία/διαγραφή ανακοινώσεων, εργασιών και εγγράφων. 

![image](https://github.com/raccoote/Educational-Website/assets/74006924/a6942021-61f4-402e-9ccd-8ff1c383d3c8)

 
**Αποστολή Email**

Στην ενότητα ‘Επικοινωνία’, το αρχείο send_email.php ελέγχει αν η αίτηση είναι τύπου POST και αποθηκεύει τα στοιχεία που υποβλήθηκαν μέσω της φόρμας (αποστολέας, θέμα, μήνυμα) σε μεταβλητές. Εκτελεί την SQL εντολή για να ανακτήσει τα ονόματα όλων των χρηστών με ρόλο "Tutor" και στέλνει email στον καθένα χρησιμοποιώντας την συνάρτηση mail().

**Τροποποίηση ανακοινώσεων,εγγράφων και εργασιών**

Ο κώδικας add_announcement.php ελέγχει αν η αίτηση που λαμβάνει είναι τύπου POST και αποθηκεύει τις τιμές που υποβάλλονται μέσω της φόρμας (θέμα, ημερομηνία, περιεχόμενο) σε μεταβλητές, όπως φαίνονται στην εικόνα δεξιά. Εκτελεί την SQL εντολή για εισαγωγή των νέων δεδομένων στον πίνακα "course_announcements" και εάν η εισαγωγή είναι επιτυχής, καθοδηγεί τον χρήστη πίσω στη σελίδα ανακοινώσεων ("announcement.php").
Σε περίπτωση σφάλματος κατά την εισαγωγή, εκτυπώνει ένα μήνυμα λάθους μαζί με την περιγραφή του σφάλματος.
Με παρόμοιο τρόπο λειτουργούν και τα add_document.php και add_homework.php. Όσο για το edit_announcement.php, το οποίο είναι υπεύθυνο για την επεξεργασία και ενημέρωση υπάρχουσας ανακοίνωσης σε έναν ιστότοπο PythonPawPals, παρατηρούμε τις εξής διαφορές σε σχέση με παραπάνω:
•	Ο κώδικας αυτός δέχεται μια παράμετρο id από το URL (μέσω $_GET['id']), το οποίο θα χρησιμοποιήσει για να ανακτήσει τα δεδομένα της ανακοίνωσης που θα επεξεργαστεί από τη βάση δεδομένων.
•	Η φόρμα επεξεργασίας συμπληρώνεται αυτόματα με τα υπάρχοντα δεδομένα της ανακοίνωσης για ευκολία επεξεργασίας.
•	Εκτελείται η SQL εντολή UPDATE αντί για INSERT για να ενημερώσει την ανακοίνωση στη βάση δεδομένων με τα νέα δεδομένα, χρησιμοποιώντας το id για τον προσδιορισμό της εγγραφής προς ενημέρωση.
Τέλος, η delete_announcement.php εκτελεί την SQL εντολή DELETE για να διαγράψει την ανακοίνωση με το id στο URL ($_GET['id']) από τον πίνακα "course_announcements". Εάν η διαγραφή είναι επιτυχής, ο χρήστης καθοδηγείται πίσω στη σελίδα ανακοινώσεων ("announcement.php") με χρήση της συνάρτησης header(). Εάν υπάρξει κάποιο σφάλμα κατά τη διαγραφή, εμφανίζεται ένα μήνυμα λάθους.


**Αυτόματη ανακοίνωση για κάθε ανάρτηση εργασιας**

Ο κώδικας add_homework.php πέρα από την προσθήκη νέας εργασίας (assignment) σε έναν ιστότοπο, χειρίζεται και την ανάρτηση μιας αυτόματης ανακοίνωσης που θα ενημερώνει τους φοιτητές, όπως φαίνεται στην παρακάτω εικόνα:
 
Λαμβάνει τα δεδομένα που υποβάλλονται μέσω της φόρμας (objectives, file_name, deliverables, submission_date).  Δημιουργεί μια SQL εντολή INSERT για την προσθήκη των νέων δεδομένων στον πίνακα "course_assignments".
Εκτελεί την SQL εντολή και, αν η προσθήκη είναι επιτυχής, προχωρά σε επιπλέον ενέργειες:
1.	Λαμβάνει την τρέχουσα ημερομηνία μέσω του date("Y-m-d").
2.	Εκτελεί μια επιπλέον SQL εντολή για την ανάκτηση του τελευταίου assignment_id που προστέθηκε στον πίνακα "course_assignments".
3.	Δημιουργεί ένα νέο θέμα ανακοίνωσης (announcement_subject) με βάση το τελευταίο assignment_id.
4.	Δημιουργεί ένα νέο περιεχόμενο ανακοίνωσης (announcement_content) που περιέχει την ημερομηνία παράδοσης της εργασίας.
5.	Δημιουργεί μια ακόμη SQL εντολή για την προσθήκη της νέας ανακοίνωσης στον πίνακα "course_announcements".
6.	Εάν και η προσθήκη της ανακοίνωσης είναι επιτυχής, ο χρήστης καθοδηγείται πάλι πίσω στη σελίδα εργασιών ("homework.php").

![image](https://github.com/raccoote/Educational-Website/assets/74006924/d109ad7b-43e2-4976-98b6-82b9d60fac17)


**Μια ματιά στην Βάση Δεδομένων**


Η βάση δεδομένων student3902.sql που δημιούργησα παρέχει έναν οργανωμένο τρόπο αποθήκευσης πληροφοριών, ομαλής λειτουργίας του ιστότοπου. Ας δούμε κάθε πίνακα αναλυτικά:
•	Χρήστες (users): Επιτρέπει την αποθήκευση και διαχείριση προσωπικών πληροφοριών χρηστών, επιτρέποντας την πρόσβαση στο σύστημα. Η μεταβλητή role είναι καθοριστική σε ολόκληρο τον ιστότοπο, καθώς είναι αυτή που καθορίζει έαν ο χρήστης έχει δικαίωμα να τροποποιεί και να διαγράφει τις αναρτήσεις.
•	Ανακοινώσεις (course_announcements): Καταγράφει τις ανακοινώσεις που γίνονται στον ιστότοπο. Κάθε ανακοίνωση περιλαμβάνει ένα μοναδικό αναγνωριστικό (announcement_id), την ημερομηνία δημοσίευσης, το θέμα της ανακοίνωσης και το περιεχόμενό της.
•	Έγγραφα (course_documents): Αντιπροσωπεύει τα έγγραφα που σχετίζονται με το μάθημα. Κάθε έγγραφο περιλαμβάνει ένα μοναδικό αριθμό αναγνώρισης (document_id), τον τίτλο του εγγράφου, μια περιγραφή και το όνομα του αρχείου.
•	Εργασίες (course_assignments): Αντιπροσωπεύει τις εργασίες που ανατίθενται στους φοιτητές. Κάθε εργασία περιλαμβάνει ένα μοναδικό αναγνωριστικό (assignment_id), τους στόχους της εργασίας χωρισμένους με κόμμα(objectives), το όνομα του αρχείου (file_name) που σχετίζεται με την εργασία, τα αναμενόμενα αποτελέσματα χωρισμένα με κόμμα (deliverables) και την ημερομηνία υποβολής (submission_date). Αυτός ο πίνακας συμβάλλει στην οργάνωση και διαχείριση των εργασιών που ανατίθενται στο πλαίσιο του μαθήματος.
Κάθε πίνακας περιέχει 10 ενδεικτικά instances, ειδικά προσαρμοσμένα για έναν ιστότοπο εκμάθησης Python με εκπαιδευτικό περιεχόμενο. Παραδείγματος χάρη, παρακάτω βλέπουμε τον πίνακα course_assignemnts:

![image](https://github.com/raccoote/Educational-Website/assets/74006924/2aafde77-cc8f-4c9d-9d32-b583cc624a07)


**Σύνδεση με την Βάση Δεδομένων**


Κάθε αρχείο php ξεκινάει με την εντολή session_start(),  η οποία εκκινεί μια νέα συνεδρία ή επαναφέρει μια υπάρχουσα συνεδρία. Στη συνέχεια, με την εντολή new mysqli γίνεται προσπάθεια σύνδεσης σε μια βάση δεδομένων MySQL, με τα στοιχεία διακομιστή, όνομα χρήστη, κωδικό πρόσβασης και όνομα βάσης. Εάν η σύνδεση αποτύχει, το πρόγραμμα τερματίζεται και εμφανίζει το μήνυμα λάθους. Στα πρώτα στάδια κατασκευής του ιστότοπου δούλεψα στον προσωπικό μου υπολογιστή μέσω XAMPP οπότε είχα θέσει το $servername= localhost. 

![image](https://github.com/raccoote/Educational-Website/assets/74006924/ba1d5ee7-edf0-4e83-bc4e-4f2271c8d0c6)

