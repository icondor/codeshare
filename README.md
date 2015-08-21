final String username = "ionel.condor@gmail.com";
        final String password = "mypassword";

        Properties props = new Properties();
        props.put("mail.smtp.auth", "true");
        props.put("mail.smtp.starttls.enable", "true");
        props.put("mail.smtp.host", "smtp.gmail.com");
        props.put("mail.smtp.port", "587");

        Session session = Session.getInstance(props,
                new javax.mail.Authenticator() {
                    protected PasswordAuthentication getPasswordAuthentication() {
                        return new PasswordAuthentication(username, password);
                    }
                });

        try {

            Message message = new MimeMessage(session);
            message.setFrom(new InternetAddress("ionel.condor@gmail.com"));
            message.setRecipients(Message.RecipientType.TO,
                    InternetAddress.parse("myemail@yahoo.com));
            message.setSubject("Num-guess");
            message.setText("Congratulation!");

            Transport.send(message);

            System.out.println("done, email sent ok");

        } catch (Exception e) {
            System.out.println("Email sending problems");
            e.printStackTrace();
        }
