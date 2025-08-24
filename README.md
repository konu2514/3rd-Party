package org.godigit.policyvault.service.impl;

import lombok.RequiredArgsConstructor;

import org.godigit.policyvault.entities.Notification;
import org.godigit.policyvault.repository.NotificationRepository;
import org.godigit.policyvault.service.NotificationService;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
@RequiredArgsConstructor
public class NotificationServiceImpl implements NotificationService {

    private final NotificationRepository notificationRepository;

    @Override
    public void createNotification(String message) {
        Notification notification = Notification.builder()
                .message(message)
                .build();
        notificationRepository.save(notification);

    }

    @Override
    public List<Notification> getAllNotifications() {
        return notificationRepository.findAllByOrderByCreatedAtDesc();
    }


}
