# BLOCKCHAIN-PROJECT-CODE
Blockchain project code on Online Voting System
package com.srawpoll;

import java.util.HashMap;
import java.util.Map;

/**
 *
 * @author Eliver 
 */
public class SrawPoll {
 private String question;
 private Map<String, Integer> options;


    public SrawPoll(String question, String... options) {
        this.question = question;
        this.options = new HashMap<>();
        for (String option : options) {
            this.options.put(option, 0);
        }
    }

    public String getQuestion() {
        return question;
    }

    public String[] getOptions() {
        return options.keySet().toArray(new String[0]);
    }

    public void vote(String option) {
        if (options.containsKey(option)) {
            options.put(option, options.get(option) + 1);
        } else {
            throw new IllegalArgumentException("Option not found: " + option);
        }
    }

    public int getResult(String option) {
        if (options.containsKey(option)) {
            return options.get(option);
        } else {
            throw new IllegalArgumentException("Option not found: " + option);
        }
    }

    public void printResults() {
        System.out.println(question);
        for (String option : options.keySet()) {
            System.out.println(option + ": " + options.get(option));
        }
    }
}Public static void main(String[] args) {
        // create a new straw poll with a question and options
        SrawPoll poll = new SrawPoll("Pick a candidate", "Candidate1", "Candidate2", "Candidate3");

        // print the question and options
        System.out.println(poll.getQuestion());
        for (String option : poll.getOptions()) {
            System.out.println(option);
        }

        // vote for an option
        poll.vote("Candidate1");
        poll.vote("Candidate2");
        poll.vote("Candidate2");
        poll.vote("Candidate2");
        poll.vote("Candidate3");
        poll.vote("Candidate3");

        // get the result of an option
        int result = poll.getResult("Candidate1");
        System.out.println("Candidate1 has " + result + " votes.");

        // print the results
        poll.printResults();
    }
